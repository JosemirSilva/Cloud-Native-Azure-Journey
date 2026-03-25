# `diagrams/`

## Propósito

Esta pasta contém **diagramas de arquitetura** e fluxos relacionados à Secure Payments API no contexto do **Azure API Management**: visão lógica do cliente até o backend, pontos de autenticação, observabilidade e segregação de ambientes.

## Formatos possíveis

- **Mermaid** em arquivos `.md` (útil para renderização em GitHub e em editores compatíveis).
- **ASCII** (diagramas em texto no próprio Markdown) quando a simplicidade for suficiente.
- **Exportações** de ferramentas visuais: **PNG**, **SVG** ou PDF gerados a partir de draw.io, Visio, PowerPoint com ícones Azure Architecture, etc.

## Diagramas disponíveis

| Arquivo | Conteúdo |
|---------|----------|
| **`secure-payments-architecture.md`** | Arquitetura **Secure Payments API**: componentes (cliente, APIM com políticas inbound/outbound, backend abstrato, Application Insights, Log Analytics) e **diagrama de sequência** requisição/resposta. |

## Relação com a documentação principal

O README raiz do lab (`../README.md`) **incorpora** o fluxo em Mermaid e **referencia** o arquivo acima como fonte versionada. Novos diagramas podem ser adicionados nesta pasta seguindo a mesma convenção (Markdown + blocos Mermaid).
