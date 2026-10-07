# Documento de Visão - FitTrack

## 1. Contexto e Problema
Atualmente, muitos praticantes de musculação e frequentadores de clubes desportivos (como ténis ou natação) registam os seus treinos de forma dispersa — seja em blocos de notas no telemóvel, papéis soltos ou folhas de cálculo complexas. Esta fragmentação dificulta o acompanhamento da progressão de cargas, a visualização da frequência semanal e a partilha de informações com profissionais de educação física (como *personal trainers*).

## 2. Justificativa
O **FitTrack** surge para centralizar a gestão da rotina desportiva num único ambiente web intuitivo. A solução facilita o registo de exercícios e cargas, automatiza o preenchimento de dados técnicos através de integração com uma API externa de exercícios e disponibiliza rotas via API REST própria para que treinadores possam acompanhar o progresso dos alunos de forma remota.

## 3. Objetivos
* Fornecer uma interface web responsiva para o cadastro e manutenção de treinos e presenças.
* Permitir a pesquisa ágil de treinos por grupo muscular, dia da semana ou duração[cite: 3].
* Consolidar relatórios mensais de volume de carga e frequência desportiva[cite: 3].
* Consumir dados da *Wger REST API* para enriquecer o catálogo de exercícios[cite: 3].
* Expor uma API REST própria para consulta de rotinas por *personal trainers*[cite: 3].

## 4. Público-Alvo e Stakeholders
* **Público-Alvo:** Praticantes de musculação, atletas amadores e sócios de clubes desportivos que desejam monitorizar a evolução física.
* **Stakeholders:** Administradores da plataforma, utilizadores finais (alunos) e *personal trainers*.

## 5. Escopo do Sistema (No Escopo)
* Cadastro completo de utilizadores, rotinas de treino, exercícios, cargas e presenças (ex: Smart Fit, Minas Brasília Tênis Clube)[cite: 3].
* Funcionalidade de busca com filtros múltiplos[cite: 3].
* Geração e exportação de relatórios de carga e frequência[cite: 3].
* Integração com a *Wger REST API* com tratamento de falhas e *timeouts*[cite: 3, 7].
* API REST própria documentada e protegida para acesso de terceiros[cite: 3, 7].

## 6. Fora do Escopo
* Aplicação móvel nativa (o acesso será feito via navegador web responsivo).
* Sistema de pagamentos integrado para cobrança de mensalidades de ginásio.
* Monitorização em tempo real de batimentos cardíacos via dispositivos *wearables* (smartwatches).

## 7. Restrições e Premissas
* **Restrições:** O backend deve ser obrigatoriamente desenvolvido em Python utilizando o framework Django[cite: 3]; a base de dados em desenvolvimento será relacional (SQLite/PostgreSQL)[cite: 3].
* **Premissas:** Os utilizadores possuem acesso à Internet através de dispositivos com navegadores modernos para aceder à aplicação publicada via HTTPS[cite: 6].

## 8. Riscos Iniciais e Mitigação
* **Risco 1:** Indisponibilidade ou instabilidade da API externa (*Wger*).
  * *Mitigação:* Implementar blocos de tratamento de exceções (*try-except*), *timeouts* e permitir o registo manual de exercícios caso a API falhe[cite: 7].
* **Risco 2:** Atrasos na publicação da aplicação web na Fase 2.
  * *Mitigação:* Definir o pipeline de deploy e testar a hospedagem de forma antecipada.

## 9. Critérios de Sucesso
* Aplicação a executar localmente e publicada com sucesso via HTTPS[cite: 6].
* Todos os requisitos funcionais mínimos (cadastro, busca, relatórios, API própria e API externa) validados e funcionais[cite: 3].
* Relatórios de segurança (SAST e DAST) executados e documentados sem falhas críticas pendentes[cite: 6, 7].