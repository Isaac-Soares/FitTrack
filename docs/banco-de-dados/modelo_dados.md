erDiagram
    USUARIO ||--o{ PRESENCA : registra
    USUARIO ||--o{ ROTINA_TREINO : possui
    USUARIO ||--o{ EVOLUCAO_CARGA : acompanha
    LOCAL_ATIVIDADE ||--o{ PRESENCA : recebe
    ROTINA_TREINO ||--o{ ROTINA_EXERCICIO : contem
    EXERCICIO ||--o{ ROTINA_EXERCICIO : compoe
    EXERCICIO ||--o{ EVOLUCAO_CARGA : tem_historico

    USUARIO {
        int id PK
        string nome
        string email
        string senha
    }

    LOCAL_ATIVIDADE {
        int id PK
        string nome "Ex: Smart Fit, Clube"
    }

    PRESENCA {
        int id PK
        datetime data_hora
        int usuario_id FK
        int local_id FK
    }

    ROTINA_TREINO {
        int id PK
        string nome
        string dia_semana
        int usuario_id FK
    }

    EXERCICIO {
        int id PK
        int wger_id "FK Externa API Wger"
        string nome
        string grupo_muscular
    }

    ROTINA_EXERCICIO {
        int id PK
        int rotina_id FK
        int exercicio_id FK
        int series
        int repeticoes
    }

    EVOLUCAO_CARGA {
        int id PK
        date data
        float carga_kg
        int usuario_id FK
        int exercicio_id FK
    }