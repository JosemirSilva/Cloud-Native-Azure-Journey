# Diagrama macro — arquitetura lógica (cloud-native)

Visão de **alto nível** dos componentes principais da solução de **aluguel de carros** na Azure: experiência do cliente, gateway e BFF, processamento assíncrono, dados, segredos e observabilidade.

> **Uso:** documentação, portfólio e alinhamento com a jornada **DIO — Cloud Native**. Não descreve dimensões de implantação (regiões, SKUs nem IaC).

```mermaid
flowchart TB
  subgraph Clientes
    U[Cliente / usuário]
  end

  subgraph Edge["Front-end"]
    FE[Interface web ou móvel\nSPA / Static Web / CDN]
  end

  subgraph Gateway["BFF e exposição de API"]
    APIM[Azure API Management\ngateway e políticas]
    BFF[BFF / API\norquestração e contratos]
  end

  subgraph Async["Mensageria e compute event-driven"]
    SB[Azure Service Bus\nfilas / tópicos]
    FA[Azure Function App\nprocessamento assíncrono]
  end

  subgraph Data["Persistência"]
    DB[(Banco de dados transacional\nAzure SQL / PostgreSQL / Cosmos)]
  end

  subgraph Secrets["Segredos centralizados"]
    KV[(Azure Key Vault)]
  end

  subgraph Obs["Observabilidade"]
    AI[Application Insights]
    LA[Log Analytics workspace]
  end

  U -->|HTTPS| FE
  FE -->|HTTPS| APIM
  APIM --> BFF
  BFF --> DB
  BFF -->|publicação de mensagens| SB
  SB -->|acionamento| FA
  FA --> DB
  BFF -.->|referências / acesso suportado| KV
  FA -.->|referências nativas em app settings\n+ Managed Identity| KV
  BFF -.->|telemetria| AI
  FE -.->|telemetria cliente| AI
  FA -.->|telemetria| AI
  APIM -.->|opcional: diagnóstico| AI
  AI --> LA
```

## Leitura rápida

- **Front-end** isola a experiência; o tráfego de API costuma passar por **API Management** antes do **BFF**.
- **Service Bus** desacopla picos e falhas entre a API síncrona e os **workers** na **Function App**.
- **Key Vault** concentra segredos; a **Function App** consome valores via **referências nativas** e **identidade gerenciada**, sem credenciais no código.
- **Application Insights** e **Log Analytics** dão visibilidade ponta a ponta.

Para o **fluxo em tempo de execução** (incluindo resolução de segredo no runtime), ver [`runtime-flow-e2e.md`](./runtime-flow-e2e.md).
