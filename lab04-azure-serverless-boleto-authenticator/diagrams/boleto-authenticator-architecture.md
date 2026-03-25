# Arquitetura e fluxo – Autenticador de boletos (serverless)

Este documento descreve o **fluxo lógico-alvo** do laboratório: mensageria **Azure Service Bus** + processamento **Azure Functions** em **Function App Consumption (Windows)** e **Application Insights**.

> **Marco atual do lab (conforme README raiz):** namespace **Service Bus** e **Function App** já estão **provisionados** no Azure; **não** há integração configurada, **não** há funções implementadas e **não** há tráfego de negócio documentado como concluído. O diagrama representa o **desenho pretendido** para as próximas etapas.

## Visão em camadas

```mermaid
flowchart TB
  subgraph In["Entrada"]
    P[Sistemas produtores\nAPI, jobs ou integrações]
  end

  subgraph Bus["Mensageria"]
    SB[Azure Service Bus\nfila ou tópico assinatura]
    DLQ[Dead-letter\napós retentativas ou rejeição]
  end

  subgraph Compute["Processamento serverless"]
    FA[Function App Consumption Windows\ntrigger Service Bus a implementar]
  end

  subgraph Obs["Observabilidade"]
    AI[Application Insights]
  end

  P -->|publica mensagem| SB
  SB -->|consumo planejado| FA
  FA -->|resultado ou próximo evento| SB
  SB -.->|mensagens com falha| DLQ
  FA -.->|telemetria| AI
```

## Fluxo no tempo (mensagem)

```mermaid
sequenceDiagram
  autonumber
  participant Prod as Produtor
  participant SB as Azure Service Bus
  participant Fn as Azure Function
  participant Obs as Application Insights

  Note over Prod,Obs: Desenho alvo após implementação e integração
  Prod->>SB: Publish mensagem autenticação de boleto
  SB->>Fn: Trigger Service Bus concluído configurado
  Fn->>Fn: Valida processa idempotência
  alt sucesso
    Fn->>SB: Enfileira resultado ou próximo passo
  else falha recuperável
    Fn->>SB: Retentativa conforme política SB
  else falha definitiva
    Fn->>SB: Dead-letter
  end
  Fn->>Obs: Logs dependências duração
```

## Leitura rápida

| Elemento | Função no autenticador |
|-----------|-------------------------|
| **Produtor** | Envia payload validação identificador ou referência de boleto. |
| **Service Bus** | Desacopla picos garante entrega e DLQ. |
| **Function** | Executa regra de autenticação sem VM dedicada. |
| **Application Insights** | Diagnóstico latência e falhas. |

---

*Mermaid compatível com o renderizador do GitHub; ajuste rótulos quando filas e nomes de função estiverem fechados.*
