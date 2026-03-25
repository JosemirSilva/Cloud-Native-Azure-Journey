# `images/`

## Propósito

Contém **evidências visuais** do laboratório **GitHub Copilot no VS Code**, alinhadas ao [`README.md`](../README.md) principal. As imagens comprovam **configuração** e **uso inicial** (em especial sugestões **inline**), não a existência de um sistema em produção.

## Prints disponíveis *(atualize conforme os arquivos reais no repositório)*

| Arquivo | O que a imagem demonstra |
|---------|-------------------------|
| **`copilot-inline-suggestion.png`** | Editor **VS Code** com **sugestão inline** do **GitHub Copilot** visível (evidência principal do uso inicial). |
| **`vscode-extensions-copilot.png`** | *(Se existir)* Painel **Extensions** com **GitHub Copilot** instalado e habilitado. |
| **`copilot-signed-in.png`** | *(Se existir)* Indicação de **conta GitHub** conectada / Copilot ativo, **sem** mostrar tokens ou URLs com segredos. |
| **`copilot-chat-panel.png`** | *(Se existir)* Painel **Chat** do Copilot aberto (evidência opcional). |

**Nota:** Se você versionar apenas o print da sugestão inline, mantenha nesta tabela somente a linha correspondente e remova ou marque como “não aplicável” as linhas opcionais nos commits seguintes.

## Checklist de privacidade *(antes de `git commit` ou entrega DIO)*

Revise **cada** PNG:

- **Tokens**, **senhas**, chaves de API ou **strings de conexão** visíveis no código, terminal ou barra de endereço do browser capturado.
- **E-mail** ou identificadores pessoais que não devam ser públicos.
- Nomes de **organização**, **repositório** ou caminhos internos sensíveis.
- Qualquer dado que permita inferir conta corporativa restrita.

**Ações:** recortar, borrar, usar captura genérica ou substituir por trecho fictício no editor antes de commitar.

## Relação com o README raiz

O **README** do lab incorpora tabela e, quando possível, pré-visualização Markdown das imagens. Mantenha **nomes de arquivo** alinhados entre esta pasta e os links no `../README.md`.
