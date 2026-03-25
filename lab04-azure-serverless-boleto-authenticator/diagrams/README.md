# `diagrams/`

## Propósito

Conter **diagramas de arquitetura** e **fluxos** do autenticador de boletos serverless: produtores, **Service Bus**, **Azure Functions**, observabilidade e tratamento de mensagens (incluindo **dead-letter**).

## Formato

- **Mermaid** em arquivos `.md` (renderização no GitHub e em editores compatíveis): `flowchart`, `sequenceDiagram`, etc.
- Opcionalmente exportações **PNG/SVG** de ferramentas visuais, se o curso ou o portfólio exigirem.

## Diagramas disponíveis

| Arquivo | Conteúdo |
|---------|----------|
| **`boleto-authenticator-architecture.md`** | Fluxo lógico-alvo: produtor → **Service Bus** → **Function App** (triggers futuros) → resultados / **DLQ**; sequência de mensagem; nota explícita de que integração e código ainda não estão no ar neste marco do lab. |

## Relação com o README principal

O [`README.md`](../README.md) incorpora o **flowchart** principal e referencia o arquivo acima para a versão completa (incluindo `sequenceDiagram`).
