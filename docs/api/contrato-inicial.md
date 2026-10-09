# **Contrato Inicial da API**

# **1\. Visão Geral e Autenticação**

A API permitirá a gestão de treinos e perfil de usuários. Ela será desenvolvida utilizando o Django REST Framework.

* **Autenticação:** Token  
* **Cabeçalho exigido:** Authorization: Token

# **2\. Endpoints**

# **Treinos (/api/treinos/)**

## **2.1. Listar Treinos do Usuário**

* **Método HTTP:** GET  
* **Endpoint:** /api/treinos/  
* **Parâmetros:** data\_inicio (opcional), data\_fim (opcional)  
* **Autenticação:** Sim  
* **Códigos de Status:** 200 (OK), 401 (Unauthorized), 400 (Bad request)

**Exemplo de Resposta (200 OK):**  
\[  
  {  
    "id": 1,  
    "titulo": "Treino de Pernas",  
    "data": "2026-10-23",  
    "duracao\_minutos": 45,  
    "calorias\_gastas": 320  
  }  
\]

## **2.2. Cadastrar Novo Treino**

* **Método HTTP:** POST  
* **Endpoint:** /api/treinos/  
* **Parâmetros:** Request body.  
* **Autenticação:** Sim  
* **Códigos de Status:** 201 (Created), 400 (Bad Request), 401 (Unauthorized)

**Exemplo de Requisição:**  
{  
  "titulo": "Corrida Matinal",  
  "data": "2026-10-24",  
  "duracao\_minutos": 30,  
  "calorias\_gastas": 250  
}

**Exemplo de Resposta (201 Created):**  
{  
  "id": 2,  
  "titulo": "Corrida Matinal",  
  "data": "2026-10-24",  
  "duracao\_minutos": 30,  
  "calorias\_gastas": 250  
}

## **2.3. Excluir Treino**

* **Método HTTP:** DELETE  
* **Endpoint:** /api/treinos/{id}/  
* **Parâmetros:** id (obrigatório, na URL)  
* **Autenticação:** Sim  
* **Códigos de Status:** 200 (OK), 401 (Unauthorized), 404 (Not Found)

# **Recurso: Usuários (/api/usuarios/)**

## **2.4. Registrar Novo Usuário**

* **Método HTTP:** POST  
* **Endpoint:** /api/usuarios/registrar/  
* **Parâmetros:** Request body  
* **Autenticação:** Não  
* **Códigos de Status:** 201 (Created), 400 (Bad Request)

**Exemplo de Requisição:**  
{  
  "nome": "Sarah J.",  
  "email": "sarah@example.com",  
  "password": "senha\_segura123"  
}

**Exemplo de Resposta (201 Created):**  
{  
"id": 1,  
"nome": "Sarah J.",  
"email": "sarah@example.com",  
"token": "abc123xyz789token..."  
}