# Arquitetura – Azure API Management (Secure Payments API)

Visão lógica do laboratório: cliente consome uma **API de pagamentos** exposta apenas através do **Azure API Management**, com políticas de governança no gateway e **observabilidade** associada.

## Visão em camadas (componentes)

```mermaid
flowchart TB
  Client["Cliente\n(app móvel, SPA ou integração B2B)"]

  subgraph APIM["Azure API Management"]
    direction TB
    Inbound["Políticas inbound\n• rate limit\n• autenticação JWT ou subscription key\n• headers obrigatórios e Idempotency-Key"]
    Outbound["Políticas outbound\n• cabeçalhos de segurança HSTS / frame / nosniff\n• remoção de metadados do servidor"]
  end

  Backend["Backend abstrato\n(API de pagamentos)"]

  subgraph Obs["Observabilidade"]
    AI["Application Insights\nmétricas, falhas, dependências"]
    LA["Log Analytics\nconsultas e diagnóstico"]
  end

  Client -->|"1. HTTPS request"| Inbound
  Inbound -->|"2. forward após validação"| Backend
  Backend -->|"3. response"| Outbound
  Outbound -->|"4. HTTPS response"| Client

  APIM -.->|"telemetria e traces"| AI
  APIM -.->|"logs e correlação"| LA
```

## Fluxo de requisição e resposta (tempo)

```mermaid
sequenceDiagram
  autonumber
  participant C as Cliente
  participant G as Azure API Management
  participant B as API de pagamentos
  participant O as App Insights e Log Analytics

  C->>G: Solicitação HTTPS
  Note over G: Rate limit, auth, validação de headers
  alt política bloqueia
    G-->>C: 401 / 400 / 429 JSON padronizado
    G->>O: evento de falha ou limite
  else política permite
    G->>B: Encaminhamento ao backend
    B-->>G: Resposta de negócio
    Note over G: Headers de segurança na saída
    G-->>C: Resposta HTTPS
    G->>O: Métricas, dependência, duração
  end
```

---

*Diagramas em Mermaid; renderize no GitHub ou em extensões compatíveis com VS Code / Cursor.*
