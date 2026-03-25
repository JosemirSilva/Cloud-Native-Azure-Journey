# `policies/`

## Propósito

No **Azure API Management**, as **políticas** são regras declarativas em **XML** que, **quando associadas a um escopo no serviço**, passam a reger o pipeline de solicitação e resposta. Elas permitem impor **segurança**, **cotas**, **autenticação** e **transformações** no gateway, alinhadas a um cenário de **API de pagamentos** sem alterar o código do backend.

> **Marco deste lab:** os XML aqui estão **documentados e versionados** no Git como **modelo de governança**; **não** declaram que já foram publicados na instância APIM provisionada — a publicação no portal ou via automação é passo posterior.

Esta pasta versiona **exemplos prontos** para revisão, cópia futura no portal ou automação em CI/CD. Cada arquivo é um documento `<policies>` completo; **ao decidir aplicar no APIM**, você pode colar o conteúdo no escopo desejado (global, produto, API ou operação) ou **fundir** trechos com o `<base />` já existente na instância.

## Arquivos

| Arquivo | Quando **for aplicar** (futuro) | Resumo |
|---------|----------------|--------|
| **`rate-limit.xml`** | API ou operações com alto risco de abuso (ex.: criação de pagamento). | **Rate limiting** por chave (exemplo: IP) com `rate-limit-by-key`. |
| **`validate-subscription-key.xml`** | Integrações B2B que usam **subscription key** do produto APIM. | Exige `Ocp-Apim-Subscription-Key`; valida **Idempotency-Key** e **Content-Type** em POST cujo path sugira pagamento. |
| **`validate-jwt.xml`** | Clientes com **OAuth2/OIDC** (ex.: token Bearer do Microsoft Entra ID). | **validate-jwt** no header `Authorization`; ajuste **TENANT_ID** e **audience** antes de uso real. |
| **`set-security-headers.xml`** | Qualquer API exposta na internet; reforço de **cabeçalhos de segurança** na resposta. | HSTS, anti-MIME-sniff, `X-Frame-Options`, `Referrer-Policy`, remoção de `Server` / `X-Powered-By` quando presentes. |
| **`custom-error-response.xml`** | Complementar o tratamento de erros do gateway (após testar em **Trace**). | Respostas **JSON** padronizadas para falhas típicas: **401** (JWT), **429** (limite), **500** genérico com header de correlação. |

## Orientações

- **Não combine** `validate-jwt.xml` e `validate-subscription-key.xml` no mesmo escopo sem um desenho explícito (por exemplo, rotas distintas ou `choose` condicional); em geral cada rota usa um modelo de autenticação.
- **`custom-error-response.xml`**: os valores de `context.LastError.Source` para quota/rate limit podem variar; valide com uma solicitação forçada no portal (**APIs** → **Test** ou **Trace**).
- **`validate-jwt.xml`**: substitua `TENANT_ID` e `api://secure-payments-api` pelos valores do seu diretório e API protegida.
- Políticas **`.xml`** devem permanecer **versionadas aqui**; alterações em produção devem refletir commits e revisão (pull request) quando aplicável.

## Exemplos futuros (ideias)

Além dos arquivos atuais, evoluções comuns em APIs de pagamento incluem: renovação de token, **IP allow list**, mascaramento de PII em logs, **caching** condicional e integração com **Application Insights** para correlação.
