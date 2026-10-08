# Arquitetura da Aplicação - FitTrack

O diagrama de arquitetura (disponível nesta pasta) ilustra a estrutura de componentes e o fluxo de dados do sistema FitTrack, baseado no padrão MVT (Model-View-Template) do framework Django.

## 1. Camadas e Responsabilidades
* **Cliente:** Divide-se em dois consumidores principais. O navegador web utilizado pelo aluno para aceder à interface gráfica (Templates HTML) e o sistema de terceiros utilizado pelo *personal trainer*, que consome dados puros via JSON[cite: 3, 21].
* **Servidor de Aplicação (Backend Django):** 
  * **URL Routing (`urls.py`):** Recebe as requisições HTTP e direciona-as para o fluxo web tradicional ou para o fluxo da API[cite: 21].
  * **Views (Lógica de Negócio):** Processa as regras da aplicação, interage com os modelos e devolve os dados para serem renderizados no HTML[cite: 21].
  * **API REST Própria (DRF):** Utiliza serializadores para converter objetos da base de dados em JSON, respondendo às requisições dos *personal trainers*[cite: 3, 21].
  * **Models (Django ORM):** Faz a abstração da base de dados, convertendo operações em código Python para consultas SQL de forma segura[cite: 21].
* **Camada de Dados:** Base de dados relacional (SQLite em desenvolvimento e PostgreSQL em produção) responsável pela persistência das rotinas, exercícios e histórico dos utilizadores[cite: 3, 21].

## 2. Integração Externa
O backend comunica ativamente com a **Wger REST API** (Serviços Externos) através de requisições HTTP REST. Esta integração permite procurar e importar dados padronizados de exercícios para a base de dados local do FitTrack, enriquecendo o cadastro das rotinas sem exigir introdução manual extensiva[cite: 3, 21].