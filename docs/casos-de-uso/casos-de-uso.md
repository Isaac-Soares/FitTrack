# Casos de Uso - FitTrack

## 1. Diagrama de Casos de Uso (UML)
*O diagrama visual em notação UML (produzido em ferramentas como draw.io ou Lucidchart) encontra-se guardado na pasta `/docs/casos-de-uso/diagrama_casos_de_uso.png` (com o respetivo ficheiro editável `.drawio`).*

---

## 2. Especificação Textual dos Casos de Uso

### UC01 - Registar Rotina de Exercício
* **Atores:** Utilizador (Praticante / Aluno).
* **Objetivo:** Criar uma nova rotina de treino, associando exercícios, séries, repetições e cargas.
* **Pré-condições:** O utilizador deve estar autenticado no sistema.
* **Pós-condições:** A rotina e os exercícios associados ficam guardados na base de dados.
* **Fluxo Principal:**
  1. O utilizador acede à secção de criação de treinos.
  2. O sistema apresenta o formulário para preenchimento (nome do treino, dia da semana, grupo muscular).
  3. O utilizador seleciona os exercícios (podendo carregar nomes padrão via integração com a *Wger REST API*).
  4. O utilizador insere as cargas e repetições planeadas e submete o formulário.
  5. O sistema valida os dados, grava a rotina e exibe uma mensagem de sucesso.
* **Fluxo Alternativo / Exceção:**
  * *Campos obrigatórios em falta:* Se o utilizador submeter sem preencher campos essenciais, o sistema rejeita o pedido e apresenta uma mensagem de erro adequada.

### UC02 - Consultar e Filtrar Treinos
* **Atores:** Utilizador.
* **Objetivo:** Pesquisar treinos registados utilizando critérios específicos.
* **Pré-condições:** O utilizador deve ter treinos previamente cadastrados.
* **Fluxo Principal:**
  1. O utilizador acede à página de listagem de treinos.
  2. O utilizador aplica filtros por grupo muscular, dia da semana ou duração.
  3. O sistema processa a busca e exibe os resultados filtrados de forma compreensível.

### UC03 - Consultar Rotina via API REST
* **Atores:** Personal Trainer (Sistema Externo / Terceiro).
* **Objetivo:** Consultar a rotina semanal de um aluno específico através de um endpoint JSON.
* **Pré-condições:** O aluno deve ter autorizado a partilha e o *personal trainer* possuir as credenciais de acesso à API.
* **Fluxo Principal:**
  1. O cliente externo envia um pedido HTTP `GET` para o endpoint da API própria do FitTrack (ex: `/api/v1/alunos/{id}/treinos/`).
  2. O sistema valida o acesso e os parâmetros.
  3. O sistema retorna os dados em formato JSON com o código de status HTTP adequado (200 OK).