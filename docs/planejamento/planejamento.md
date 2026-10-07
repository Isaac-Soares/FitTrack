# Planeamento e Backlog - FitTrack

## 1. Estratégia de Execução até à Fase 2
O projeto será desenvolvido de forma incremental até à entrega da Fase 2, dividindo as tarefas técnicas entre os elementos do grupo. O controlo do progresso será efetuado através de issues e milestones no GitHub, garantindo que todos os elementos contribuem com *commits* identificáveis[cite: 2].

## 2. Backlog do Projeto (Tarefas e Responsáveis)

| ID | Tarefa / Funcionalidade | Descrição Resumida | Responsável | Marco / Prazo |
|----|-------------------------|---------------------|-------------|---------------|
| T01 | Configuração do Ambiente | Inicializar projeto Django, estruturação de apps e base de dados. | Thiago Moura | Semana 1 |
| T02 | Modelos de Dados (Models) | Criar models para Utilizador, Treino, Exercício, Cargas e Presenças. | Thiago Moura | Semana 2 |
| T03 | Funcionalidade de Cadastro | Implementar views, formulários e templates para criar/editar treinos e cargas[cite: 3]. | Isaac Faria | Semana 3 |
| T04 | Funcionalidade de Busca | Desenvolver filtros de pesquisa por grupo muscular, dia e duração[cite: 3]. | Isaac Faria | Semana 3 |
| T05 | Relatórios e Exportação | Criar lógica para consolidar volume de carga mensal e exportação de dados[cite: 3]. | Isaac Faria | Semana 4 |
| T06 | Integração com API Externa | Consumir a *Wger REST API* para pré-carregar nomes e instruções de exercícios[cite: 3, 7]. | Tales Pessoa | Semana 4 |
| T07 | Desenvolvimento da API REST | Criar endpoints próprios (Django REST Framework) para consulta de rotinas por personal trainers[cite: 3]. | Tales Pessoa  | Semana 5 |
| T08 | Testes e Qualidade | Escrever testes unitários e funcionais dos fluxos críticos. | Todos | Semana 6 |
| T09 | Análise de Segurança (SAST/DAST) | Executar ferramentas como Bandit e OWASP ZAP, documentando e corrigindo falhas[cite: 6, 7]. | Todos | Semana 6 |
| T10 | Publicação (Deploy) | Publicar a aplicação em servidor cloud com HTTPS e variáveis de ambiente seguras[cite: 6]. | Thiago Moura | Semana 7 |