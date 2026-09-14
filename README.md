# CoffeeAI Desktop — Downloads

![Versão 0.3.0-alpha.21](https://img.shields.io/badge/vers%C3%A3o-0.3.0--alpha.21-C87941)
![Windows x64](https://img.shields.io/badge/plataforma-Windows%20x64-5D4037)

**Baixe o CoffeeAI para reunir Codex, Claude e Gemini em um único aplicativo local para Windows.**

[**⬇ Baixar CoffeeAISetup.exe**](https://github.com/Hyant4/CoffeeAI-Desktop-Releases/releases/download/v0.3.0-alpha.21/CoffeeAISetup.exe)
·
[Ver a release v0.3.0-alpha.21](https://github.com/Hyant4/CoffeeAI-Desktop-Releases/releases/tag/v0.3.0-alpha.21)
·
[Todas as versões](https://github.com/Hyant4/CoffeeAI-Desktop-Releases/releases)

> [!WARNING]
> O CoffeeAI está em fase alpha e o instalador ainda não possui assinatura digital. O Windows
> SmartScreen pode exibir um aviso. Verifique o SHA-256 publicado na mesma release antes de
> executar o arquivo.

## O que é o CoffeeAI

O CoffeeAI é um desktop local para conversar e trabalhar com agentes de código. Ele organiza
conversas, equipes, contexto, Skills, projetos Git, worktrees, diffs e aprovações sem exigir uma
conta própria, navegador ou servidor localhost.

- Use Codex, Claude e Gemini na mesma interface.
- Pergunte em modo somente leitura ou execute mudanças em worktrees isolados.
- Monte equipes com até quatro perfis de agente.
- Revise o progresso e o diff antes de aplicar, commitar, enviar ou abrir um pull request.
- Mantenha conversas, configurações e contexto no seu computador.

## Requisitos

| Item | Quando é necessário |
| --- | --- |
| Windows x64 | Para instalar e executar o aplicativo. |
| Codex, Claude Code ou Gemini CLI | Ao menos um deles deve estar instalado e autenticado. |
| Git | Para trabalhar em repositórios e usar o modo Executar. |
| GitHub CLI (`gh`) | Somente para importar projetos ou publicar no GitHub. |
| Node.js | Pode ser exigido pela forma de instalação de alguns CLIs. |

O setup já inclui o Electron e o engine Python. **Não é necessário instalar Python ou `uv`**
para usar o aplicativo. Os CLIs e suas autenticações são independentes; o setup não instala
nem faz login em serviços de terceiros.

## Como instalar

1. Baixe o [**CoffeeAISetup.exe**](https://github.com/Hyant4/CoffeeAI-Desktop-Releases/releases/download/v0.3.0-alpha.21/CoffeeAISetup.exe).
2. Baixe também `CoffeeAISetup.exe.sha256` na
   [mesma release](https://github.com/Hyant4/CoffeeAI-Desktop-Releases/releases/tag/v0.3.0-alpha.21)
   e confira a integridade do instalador.
3. Feche uma instalação anterior do CoffeeAI e execute o setup com sua conta normal do Windows.
4. Abra **CoffeeAI** pelo Menu Iniciar ou pelo atalho da Área de Trabalho.
5. Em **Configurações → Agentes e CLIs**, confira os provedores detectados e conclua a
   autenticação no CLI que deseja usar.

A instalação é feita por usuário em `%LOCALAPPDATA%\CoffeeAIDesktop`, sem exigir privilégios de
administrador nem perguntar uma pasta de destino.

## Verificar o download

Abra o PowerShell na pasta dos arquivos baixados e execute:

```powershell
$expectedHash = (Get-Content .\CoffeeAISetup.exe.sha256).Split()[0].ToLowerInvariant()
$downloadHash = (Get-FileHash .\CoffeeAISetup.exe -Algorithm SHA256).Hash.ToLowerInvariant()
$downloadHash -eq $expectedHash
```

O resultado deve ser `True`. Se for `False`, não execute o instalador: apague os dois arquivos e
faça o download novamente pela página da release.

## Atualizações

Depois da instalação inicial, o CoffeeAI pode consultar e baixar novas versões em segundo plano.
Quando uma atualização estiver pronta, o aplicativo oferece **Reiniciar para atualizar** ou
**Depois**. Ele não reinicia durante uma execução, subprocesso ou aprovação pendente.

Os canais alpha e estável, assim como as preferências de consulta e download automáticos, ficam em
**Configurações → Atualizações**. A primeira versão com o atualizador integrado precisa ser
instalada manualmente.

## Desinstalação e dados

Use **Configurações do Windows → Aplicativos → Aplicativos instalados → CoffeeAI → Desinstalar**.
O programa e seus atalhos serão removidos, mas conversas, configurações e backups permanecerão
em `%LOCALAPPDATA%\CoffeeAI\data`. Seus repositórios Git continuam nas pastas originais. Uma
reinstalação pode reutilizar esses dados.

## Arquivos de cada release

| Arquivo | Finalidade |
| --- | --- |
| `CoffeeAISetup.exe` | Instalador recomendado para o usuário. |
| `CoffeeAISetup.exe.sha256` | Checksum do instalador. |
| `RELEASES` | Manifesto usado pelo atualizador integrado. |
| `CoffeeAIDesktop-*-full.nupkg` | Pacote completo usado pelo Squirrel.Windows. |
| `*.sha256` | Checksums dos artefatos de distribuição. |

Este repositório público contém somente os arquivos de distribuição. O código-fonte e o
desenvolvimento do aplicativo permanecem no repositório privado do projeto.
