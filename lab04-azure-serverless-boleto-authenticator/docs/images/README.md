# `docs/images/`

## Propósito

Armazenar **evidências** do laboratório no **Azure Portal**: recursos provisionados que sustentam o desenho serverless do autenticador de boletos, sem substituir a documentação textual do repositório.

## Imagens versionadas

| Arquivo | Descrição breve |
|---------|------------------|
| **`Service-Bus-Creating.png`** | Fluxo de criação ou visão do **Azure Service Bus** no portal (provisionamento do namespace / recurso). |
| **`funcapp-creating.png`** | Fluxo de criação ou detalhes da **Function App** (Consumption, Windows) no portal. |
| **`resources-funcapp-servicebus.png`** | Visão de **recursos relacionados** no resource group (Function App, Service Bus e demais itens do lab), compondo o contexto de infraestrutura. |

*(Nomes de arquivo preservados conforme adicionados ao repositório; referencie sempre com a mesma capitalização no Markdown.)*

## Prints adicionais (opcional)

Você ainda pode complementar com **Application Insights** ou outras lâminas, desde que passem pelo checklist abaixo.

## Checklist antes de `git commit` ou entrega (DIO / portfólio)

Revise **cada** imagem e borre ou recorte, se necessário:

- **Subscription ID**, **tenant ID**, IDs de recurso completos em URL ou blade.
- **Connection strings**, SAS, chaves de Service Bus, *instrumentation keys* ou segredos de Function App.
- Dados pessoais, nomes internos sensíveis ou informações contratuais.

Objetivo: provar **o que foi provisionado**, não **executar** nem simular um fluxo que ainda não existe no código.

## Lista no README principal

O [`README.md`](../README.md) do lab incorpora pré-visualização dessas evidências para portfólio no GitHub.
