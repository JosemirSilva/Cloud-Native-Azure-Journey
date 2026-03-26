# `diagrams/`

## Propósito

Centralizar **diagramas** em **Mermaid** que ilustram a arquitetura **cloud-native** de **aluguel de carros**, o **fluxo em runtime** e a integração com **Azure Key Vault** documentada no Lab06.

## Diagramas disponíveis

| Arquivo | Propósito |
|---------|-----------|
| **`logical-architecture-macro.md`** | **Arquitetura lógica (macro):** *flowchart* com cliente, front-end, **API Management**, BFF, **Service Bus**, **Function App**, banco de dados, **Key Vault** e **Application Insights** / **Log Analytics**. Adequado para visão de portfólio e apresentações de alto nível. |
| **`runtime-flow-e2e.md`** | **Fluxo fim a fim (runtime):** *sequenceDiagram* da requisição do usuário até notificação, incluindo enfileiramento, processamento na **Function App**, obtenção de segredos via **Key Vault** com **Managed Identity** e persistência. |
| **`car-rental-architecture.md`** | **Visão consolidada (legado):** diagrama de componentes + sequência simplificada de reserva e texto explicativo; mantido para alinhamento com versões anteriores da documentação do lab. |

## Relação com o README principal

O [`README.md`](../README.md) na raiz do Lab06 referencia estes arquivos, resume a arquitetura em linguagem corrida e detalha **segurança**, **identidade** e **evidências** em [`images/`](../images/).
