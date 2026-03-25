# `messaging/`

## Azure Service Bus no portal

O **namespace do Azure Service Bus** utilizado neste laboratório **já foi provisionado** via **Azure Portal**. Este repositório descreve o **papel esperado** da mensageria; não substitui o painel de administração nem afirma nomes de entidades até que sejam documentados em evoluções futuras.

## Papel esperado no fluxo de autenticação de boletos

O barramento deve **desacoplar** quem **emite** pedidos ou eventos relacionados a boletos (produtores) de quem **processa** (futuras **Azure Functions** na Function App já criada). Espera-se que:

- Mensagens carreguem **dados ou referências** suficientes para validação/autenticação conforme regras do lab.
- O processamento **assíncrono** permita escalar o consumo sem dimensionar manualmente o produtor.
- **Falhas** possam ser tratadas com retentativas e, quando aplicável, encaminhamento para **dead-letter**, evitando perda silenciosa de solicitações.

**Não há**, neste estágio, integração configurada entre a Function App e o Service Bus nem processamento real de filas descrito como em execução.

## Padrões possíveis (sem fixar nomes ainda)

As entidades concretas (**filas**, **tópicos**, **subscriptions**, nomes exatos) **não são assumidas** nesta documentação: ficam a cargo do desenho da próxima fase do lab. Em termos de modelo:

| Ideia | Quando pode fazer sentido |
|-------|----------------------------|
| **Fila** | Pipeline simples: uma mensagem, um fluxo de autenticação por fatia de trabalho. |
| **Tópico + assinaturas** | Vários consumidores com papéis distintos (ex.: validação principal vs. auditoria). |
| **Dead-letter** | Inspeção de mensagens inválidas ou que esgotaram retentativas. |

Detalhes de contrato (schema, cabeçalhos, versionamento) poderão ser adicionados aqui **sem** publicar connection strings ou segredos.
