# Diagrama — fluxo fim a fim (runtime)

Sequência **ilustrativa** de uma operação (ex.: **criação de reserva** ou evento de domínio equivalente): caminho síncrono até o BFF, enfileiramento, processamento na **Function App**, **leitura de configuração/segredos** via **Key Vault** com **Managed Identity**, persistência e notificação.

> **Nota:** o passo **Key Vault** representa a **resolução em runtime** de referências `@Microsoft.KeyVault(SecretUri=...)` nas **Application Settings** (ou acesso via SDK/credencial gerenciada, conforme o projeto). O segredo **não** trafega pela definição da variável no portal/CLI — apenas o **URI** do segredo referenciado.

```mermaid
sequenceDiagram
  autonumber
  participant U as Cliente / usuário
  participant FE as Front-end
  participant APIM as API Management
  participant BFF as BFF / API
  participant SB as Azure Service Bus
  participant FA as Azure Function App
  participant KV as Azure Key Vault
  participant DB as Banco de dados
  participant NT as Notificações

  U->>FE: Ação na interface (ex.: confirmar reserva)
  FE->>APIM: HTTPS (token / políticas)
  APIM->>BFF: Encaminha requisição validada
  BFF->>DB: Leitura/gravação transacional (caminho síncrono)
  BFF->>SB: Publica mensagem de domínio (evento)
  BFF-->>FE: Resposta HTTP (ex.: 202 / confirmação recebida)
  FE-->>U: Atualização da UI

  SB->>FA: Entrega mensagem ao worker
  Note over FA,KV: Na inicialização ou em runtime,\nFunction App resolve @Microsoft.KeyVault(...)\nusando Managed Identity + RBAC
  FA->>KV: Obtém material secreto (connection strings, chaves)\nvia identidade gerenciada
  KV-->>FA: Segredo (TLS, escopo autorizado)
  FA->>DB: Persistência / atualização de estado
  FA->>NT: Dispara notificação (e-mail, SMS, webhook)
  NT-->>U: Comunicação assíncrona ao usuário (canal externo)
```

## Pontos de segurança no fluxo

1. **Borda:** **APIM** concentra autenticação de consumidores, limites e políticas antes do BFF.
2. **Segredos:** o runtime da **Function App** acessa o **Key Vault** como **Service Principal** da identidade gerenciada (**Key Vault Secrets User** no escopo do cofre ou mais restritivo, conforme política).
3. **Superfície de configuração:** **Application Settings** armazenam a **referência**, não o valor do segredo em texto claro.

Para a **visão estática de componentes**, ver [`logical-architecture-macro.md`](./logical-architecture-macro.md).
