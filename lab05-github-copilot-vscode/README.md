# Lab05 – GitHub Copilot no Visual Studio Code

## Objetivo do projeto

Este projeto **documenta**, de forma simples e reproduzível, o **uso do GitHub Copilot no Visual Studio Code**: **instalação da extensão**, **autenticação** com GitHub, **ativação** do serviço e **uso inicial com sugestões inline**. O repositório existe para **evidências e racional técnico** (entrega **DIO** / portfólio na jornada Cloud Native).

**Escopo da entrega:** apenas **documentação** (`README`, pasta `images/`). **Não** há aplicação executável, **não** há projeto funcional avaliado como produto nem fluxo de negócio implementado neste lab — eventual arquivo local de experimento no editor **não** constitui entrega de software.

## Ambiente utilizado

| Componente | Descrição |
|------------|-----------|
| **Visual Studio Code** | Editor com integração às extensões da marketplace. |
| **GitHub Copilot** | Assistente de código via extensão oficial, dependente de conta **GitHub** e plano Copilot. |

## Processo de configuração *(concluído neste lab)*

Os passos abaixo descrevem o fluxo realizado e confirmado no ambiente do autor; servem como guia para quem reproduzir o laboratório.

### 1. Extensão instalada

1. Abrir o **VS Code**.
2. **Extensions** (`Ctrl+Shift+X` no Windows/Linux, `Cmd+Shift+X` no macOS).
3. Buscar **GitHub Copilot** (publicadora GitHub) e instalar a extensão (e dependências indicadas, se houver).

### 2. Autenticação com GitHub

1. Completar **Sign in with GitHub** quando o VS Code solicitar.
2. Autorizar o **Visual Studio Code** no fluxo do navegador.
3. Garantir **assinatura Copilot** ativa na conta (Individual, Business ou período de avaliação, conforme o caso).

### 3. Ativação do Copilot

1. Confirmar ícone/estado do **Copilot** na barra de status ou via **Command Palette** (`Ctrl+Shift+P` / `Cmd+Shift+P`).
2. Em **Settings**, revisar opções `github copilot` (habilitado globalmente ou no workspace).

### 4. Uso de sugestões inline

1. Em um arquivo de código ou texto, digitar comentário ou trecho inicial; aguardar **sugestão inline** (texto em destaque cinza).
2. **Aceitar** com `Tab` ou **dispensar** com `Esc`, conforme a relevância da sugestão.
3. **Revisar sempre** o conteúdo sugerido antes de considerar o trecho como válido (correção, licença, dados sensíveis).

> **Chat Copilot** (painel lateral) é opcional neste lab; o foco da evidência principal é **sugestão inline**.

## Insights e aprendizados

### Benefícios percebidos

- Ganho de **produtividade** em código repetitivo e exploração de sintaxe.
- **Aprendizado** com sugestões contextualizadas ao arquivo aberto.
- **Fluxo contínuo** no VS Code, sem ferramentas externas obrigatórias.

### Limitações percebidas

- Sugestões podem estar **erradas** ou **desatualizadas** face à documentação oficial.
- **Contexto** limitado ao que o modelo inferir; não substitui revisão humana.
- **Não** expor segredos no prompt ou em comentários que alimentem o modelo.

### Boas práticas

- Usar Copilot como **assistente**; validar criticamente.
- Evitar colar **tokens**, **senhas** ou **dados pessoais** no editor/chat.
- Combinar com **revisão de código** em projetos reais.

## Evidências

Os prints ficam em **`images/`**. Neste lab, há evidência de **sugestão inline** no editor; demais capturas são complementares, se existirem.

| # | Arquivo | O que demonstra |
|---|---------|------------------|
| 1 | `copilot-inline-suggestion.png` | **GitHub Copilot** exibindo **sugestão inline** no VS Code (uso inicial confirmado). |
| 2 | `vscode-extensions-copilot.png` | *(Opcional)* Extensão **GitHub Copilot** instalada na lista do VS Code. |
| 3 | `copilot-signed-in.png` | *(Opcional)* Sessão **GitHub** / Copilot ativa, sem expor credenciais. |

Detalhes e **checklist de privacidade**: [`images/README.md`](./images/README.md).

### Pré-visualização *(se o arquivo estiver no repositório com este nome)*

![Sugestão inline do GitHub Copilot no VS Code](./images/copilot-inline-suggestion.png)

*Se o seu print usar **outro nome de arquivo**, ajuste o caminho acima ou renomeie o PNG para `copilot-inline-suggestion.png`.*

---

*Documentação elaborada com apoio de ferramentas de IA e sujeita à revisão no contexto do bootcamp Dio — Cloud Native no Azure.*
