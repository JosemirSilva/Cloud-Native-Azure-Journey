# `api/`

Esta pasta é dedicada ao **contrato da API** no formato **OpenAPI** (especificação anteriormente conhecida como **Swagger**): paths, operações, parâmetros, esquemas de dados e, quando fizer sentido, exemplos de requisição e resposta.

## Propósito no lab

- Definir de forma **versionável** o que consumidores e o **Azure API Management** enxergam como superfície da **Secure Payments API**.
- Apoiar importação ou sincronização da API no APIM a partir de um artefato explícito no repositório.

## Escopo explicitamente **fora** desta pasta

- **Não há backend implementado neste laboratório** nesta etapa: nenhum projeto executável (por exemplo .NET, Node ou Java) deve ser tratado como parte de `api/`.
- O foco do lab é **governança** (contrato claro, evolução controlada) e **exposição segura via Azure API Management**, não a lógica de negócio em servidor de aplicação.

## Conteúdo esperado (quando o escopo avançar)

- Arquivo(s) **OpenAPI 3.x** em YAML ou JSON.
- Notas sobre versionamento de URL (`/v1/...`), códigos de erro padronizados e convenções de nomenclatura.
