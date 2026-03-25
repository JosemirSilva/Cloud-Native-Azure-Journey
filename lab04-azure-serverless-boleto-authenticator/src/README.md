# `src/`

## Contexto na Azure

A **Function App** do laboratório **já existe** no Azure (**plano Consumption**, host **Windows**). Ela serve de **destino de implantação** futura para o código que será mantido nesta pasta.

**Neste estágio:** não há funções implementadas na app nem projeto de desenvolvimento versionado aqui; nenhum trigger (incluindo Service Bus) foi configurado em código.

## Propósito

Esta pasta receberá o **código da solução serverless** com **Azure Functions**: handlers que, em etapas posteriores, poderão ser acionados por mensagens do **Azure Service Bus** ou por outros gatilhos autorizados pelo desenho do produto.

## Responsabilidades esperadas da camada serverless (quando implementadas)

- **Consumir** mensagens que representem solicitações ou eventos de **autenticação / validação de boletos** (conteúdo e formato a definir em `messaging/`).
- Aplicar **regras de negócio e validação** (formato, consistência, integrações externas) sem acoplar a lógica ao produtor da mensagem.
- **Publicar** resultados (sucesso, falha ou eventos downstream) de forma segura para filas/tópicos ou outros destinos acordados.
- Respeitar **idempotência**, **retentativas** e uso de **dead-letter** oferecidos pelo Service Bus, tratando falhas de forma observável (Application Insights).

## Estado atual

**Sem implementação** neste diretório: nenhum projeto (por exemplo `.csproj`, `host.json`, `local.settings.json` com segredos) foi adicionado. A escolha de stack de runtime na Function App Windows será alinhada ao projeto quando o desenvolvimento for iniciado.
