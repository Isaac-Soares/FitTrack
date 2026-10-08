# Arquitetura do Sistema FitTrack

## 1. Diagrama de Componentes

```mermaid
graph TD
    subgraph Cliente
        UI[Navegador Web / Mobile]
        PT[Sistema de Terceiros / Personal Trainer]
    end

    subgraph Servidor de Aplicação FitTrack
        subgraph Backend Django
            URLs[URL Routing / urls.py]
            Views[Views / Lógica de Negócio]
            Templates[Templates HTML / Interface]
            Models[Models / Django ORM]
            API_Interna[API REST Própria / DRF]
        end
    end

    subgraph Camada de Dados
        DB[(Banco de Dados Relacional)]
    end

    subgraph Serviços Externos
        API_Wger[Wger REST API]
    end

    %% Interação do Usuário (Interface)
    UI -->|1. Requisição HTTP| URLs
    URLs -->|2. Roteamento Web| Views
    Views -->|3. Processa e Renderiza| Templates
    Templates -->|4. Resposta HTML| UI
    
    %% Consumo da API Externa
    Views <-->|Requisição HTTP REST| API_Wger

    %% Interação do Personal Trainer (API)
    PT -->|1. Requisição HTTP / JSON| URLs
    URLs -->|2. Roteamento API| API_Interna
    API_Interna -->|3. Resposta JSON| PT

    %% Persistência de Dados
    Views <-->|Consulta/Atualiza| Models
    API_Interna <-->|Serialização| Models
    Models <-->|SQL| DB