# `images/`

## Propósito

Evidências visuais do Lab06: **Key Vault**, **Function App** (Managed Identity, Application Settings com referências), **RBAC** — para entrega **DIO** e portfólio.

Os diagramas em Mermaid estão em [`diagrams/`](../diagrams/).

## Arquivos padronizados (nomes da tabela do README principal)

| Arquivo | Estado | Conteúdo esperado |
|---------|--------|-------------------|
| **`lab06-keyvault-overview.png`** | Captura real | Visão do **Key Vault** (nome, resource group, modelo RBAC). |
| **`lab06-keyvault-secrets.png`** | Captura real | Lista de **segredos** (nomes visíveis; valores não expostos). |
| **`lab06-functionapp-managed-identity.png`** | Captura real | Function App com **System assigned identity** / **Object ID** visível (ajuste a captura se necessário para destacar a folha **Identity**). |
| **`lab06-keyvault-rbac-role-assignment.png`** | **Placeholder** | Substitua por **Access control (IAM)** do cofre: **Key Vault Secrets User** para o principal da Function App. |
| **`lab06-functionapp-appsettings-keyvault-ref.png`** | **Placeholder** | Substitua por **Configuration → Application settings** com variáveis `@Microsoft.KeyVault(SecretUri=...)`. |

## Privacidade antes do `git commit`

- Revisar **subscription ID**, **tenant ID**, nomes internos e dados pessoais.
- Recortar ou borrar o necessário para repositório público.
