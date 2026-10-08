# Modelo de Dados - FitTrack

O modelo relacional do projeto (ilustrado no diagrama ER anexo nesta pasta) descreve as entidades necessárias para o funcionamento do sistema e a relação entre elas, desenhadas para garantir a integridade da monitorização física do utilizador.

## 1. Entidades Principais e Atributos

### 1.1 USUARIO
Armazena os dados de autenticação e contacto dos utilizadores e *personal trainers*.
* `id` (INT, Primary Key): Identificador único.
* `nome` (STRING): Nome completo do praticante.
* `email` (STRING, Unique): Endereço de email para login e contacto.
* `senha` (STRING): Hash da palavra-passe.

### 1.2 ROTINA_TREINO
Representa as fichas ou programas de treino criados pelo utilizador.
* `id` (INT, Primary Key): Identificador único do treino.
* `nome` (STRING): Ex: "Treino de Hipertrofia", "Treino A".
* `dia_semana` (STRING): Dia em que a rotina é planeada.
* `usuario_id` (INT, Foreign Key): Referência ao utilizador que criou o treino.

### 1.3 EXERCICIO
Catálogo global de exercícios, que pode ser enriquecido através da integração com a API externa.
* `id` (INT, Primary Key): Identificador único no nosso sistema.
* `wger_id` (INT, Nullable): Identificador externo mapeado a partir da *Wger REST API* (se aplicável).
* `nome` (STRING): Nome do exercício (ex: "Supino Inclinado").
* `grupo_muscular` (STRING): Ex: "Peito", "Costas".

### 1.4 ROTINA_EXERCICIO (Tabela Associativa)
Faz a ligação entre os treinos criados e os exercícios, guardando as séries e as repetições planeadas para cada ficha.
* `id` (INT, Primary Key): Identificador único.
* `rotina_id` (INT, Foreign Key): Referência à tabela ROTINA_TREINO.
* `exercicio_id` (INT, Foreign Key): Referência à tabela EXERCICIO.
* `series` (INT): Número de séries planeadas.
* `repeticoes` (INT): Número de repetições por série.

### 1.5 EVOLUCAO_CARGA
Tabela de histórico para acompanhar o peso (carga) utilizado pelo aluno ao longo do tempo. Essencial para a geração de relatórios de progressão.
* `id` (INT, Primary Key): Identificador único do registo.
* `data` (DATE): Dia em que o registo foi feito.
* `carga_kg` (FLOAT): Peso levantado no momento.
* `usuario_id` (INT, Foreign Key): Aluno que registou a carga.
* `exercicio_id` (INT, Foreign Key): Exercício correspondente.

### 1.6 LOCAL_ATIVIDADE e PRESENCA
Controlam a assiduidade dos alunos em ginásios e clubes desportivos.
* **LOCAL_ATIVIDADE**: 
  * `id` (INT, PK), `nome` (STRING) - Ex: "Smart Fit", "Minas Brasília Tênis Clube".
* **PRESENCA**:
  * `id` (INT, PK), `data_hora` (DATETIME), `usuario_id` (INT, FK), `local_id` (INT, FK).

## 2. Cardinalidades e Relacionamentos Relevantes
* **1:N (Um para Muitos):**
  * Um `USUARIO` possui muitas `ROTINA_TREINO`.
  * Um `USUARIO` regista muitas entradas na `EVOLUCAO_CARGA`.
  * Um `USUARIO` regista várias entradas de `PRESENCA` em um ou mais `LOCAL_ATIVIDADE`.
* **N:M (Muitos para Muitos) resolvido com tabela associativa:**
  * Uma `ROTINA_TREINO` contém muitos `EXERCICIO`, e um `EXERCICIO` pode estar em muitas `ROTINA_TREINO`. A ligação é feita através da tabela `ROTINA_EXERCICIO` que guarda as `series` e `repeticoes` específicas dessa combinação.

## 3. Restrições e Normalização
O modelo encontra-se na Terceira Forma Normal (3FN), garantindo que não há redundância (por exemplo, as séries e repetições dependem exclusivamente da relação Treino-Exercício). Os *Foreign Keys* garantirão a integridade referencial através do Django ORM com a política de apagamento em cascata (`on_delete=models.CASCADE`) nas relações de dependência forte, como entre `ROTINA_TREINO` e `ROTINA_EXERCICIO`.