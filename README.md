# 🏋️‍♂️ FitTrack

**FitTrack** é uma plataforma web para monitorização de treinos, evolução física e gestão de atividades em clubes desportivos. 

## 🎯 Problema e Público-Alvo
Muitos praticantes de exercício físico enfrentam dificuldades para manter um registo unificado da sua progressão de cargas e frequência desportiva. O público-alvo do sistema são os frequentadores de ginásios, atletas amadores e membros de clubes que necessitam de centralizar a sua evolução física, deixando de depender de anotações em papel ou aplicações fragmentadas.

## ✨ Principais Funcionalidades
* **Cadastro:** Criação de rotinas de treino, registo de exercícios, evolução de cargas e histórico de presenças nos locais de atividade (como por exemplo, a rotina de musculação na Smart Fit ou as idas ao Minas Brasília Tênis Clube).
* **Busca:** Pesquisa de treinos filtrados por grupo muscular, dia da semana ou duração.
* **Relatórios:** Exportação do volume total de carga levantada por mês e estatísticas de frequência do utilizador.
* **Integração de API Externa:** Consumo da base de dados *Wger REST API* para pré-carregar instruções detalhadas e nomes padrão de exercícios.
* **API REST Própria:** Endpoint JSON que permite aos *personal trainers* consultarem, de forma remota, a rotina semanal de um aluno específico.

## 👥 Integrantes do Grupo
* Isaac Faria Soares
* Thiago Moura 
* Tales Pessoa

## 💻 Tecnologias Empregadas
* **Linguagem:** Python
* **Framework Web:** Django
* **API:** Django REST Framework
* **Base de Dados:** SQLite (Desenvolvimento) / PostgreSQL (Produção)
* **Frontend:** HTML5, CSS3, JavaScript e Django Templates

## 🚀 Instruções para Configuração e Execução Local
1. Clone este repositório:
   `git clone [URL_DO_SEU_REPOSITORIO]`
2. Crie e ative o ambiente virtual:
   `python -m venv venv`
   * Windows: `venv\Scripts\activate`
   * Linux/Mac: `source venv/bin/activate`
3. Instale as dependências:
   `pip install -r requirements.txt`
4. Execute as migrações da base de dados:
   `python manage.py migrate`
5. Inicie o servidor de desenvolvimento:
   `python manage.py runserver`

## 🔐 Variáveis de Ambiente Necessárias
O projeto requer a configuração das seguintes variáveis de ambiente no ficheiro `.env` (utilize o ficheiro `.env.example` como base e **nunca submeta valores reais no repositório**):
* `SECRET_KEY`: Chave de segurança do Django.
* `DEBUG`: Define o modo de depuração (True/False).
* `ALLOWED_HOSTS`: Domínios permitidos.
* `DATABASE_URL`: String de conexão com o banco de dados.

## 🔗 Links Úteis e Situação Atual
* **Situação Atual:** Fase 1 (Arquitetura e Documentação) em andamento.
* **Link da Aplicação Publicada:** *(A ser definido na Fase 2)*
* **Documentação da API REST:** *(A ser definido na Fase 2)*

## 📄 Licença
Este projeto foi desenvolvido para fins académicos e tem licenciamento livre.
