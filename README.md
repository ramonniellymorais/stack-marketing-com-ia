# Stack de marketing com IA

O que está instalado no meu Mac e para que cada coisa serve no trabalho de conteúdo.

Não é lista de "as 50 melhores ferramentas". É o que sobrou depois de um ano testando, organizado pelo problema que resolve — porque a pergunta útil nunca foi "qual ferramenta usar", foi "o que está me travando hoje".

Sou estrategista de conteúdo, não desenvolvedora. Tudo aqui foi instalado por alguém que aprendeu no caminho, e está escrito para quem também vai aprender no caminho.

---

## Como ler esta lista

Cada linha tem o que a coisa é, o problema de conteúdo que ela resolve e como instalar.

| Marca | Significa |
|---|---|
| **Todo dia** | Abro sem pensar. Se sumisse amanhã, o dia trava. |
| **Toda semana** | Entra no ritual semanal de produção. |
| **Quando precisa** | Fica quieta até o dia em que salva a operação. |

Tudo roda em macOS (Apple Silicon). A maioria funciona em Linux sem mudança; no Windows, o caminho é o WSL.

---

## 1. Pensar e escrever

| Ferramenta | Uso | O que resolve |
|---|---|---|
| **[Claude Code](https://claude.com/claude-code)** | Todo dia | O centro da operação. Roda no terminal, lê os arquivos do projeto, escreve, edita, executa. A diferença para o chat no navegador é que ele enxerga a pasta inteira do cliente — o contexto não precisa ser colado toda vez. |
| **[Gemini CLI](https://github.com/google-gemini/gemini-cli)** | Quando precisa | Segunda opinião e janela de contexto maior para ler transcrição gigante de uma vez. Bom para conferir se a primeira leitura deixou coisa para trás. |

```bash
npm install -g @anthropic-ai/claude-code
npm install -g @google/gemini-cli
```

---

## 2. Transformar áudio e vídeo em texto

O maior desperdício de matéria-prima em marketing de conteúdo é a reunião gravada que ninguém abre. Aula, mentoria, live, call de briefing: tudo isso é banco narrativo trancado dentro de um arquivo de mídia.

| Ferramenta | Uso | O que resolve |
|---|---|---|
| **[WhisperX](https://github.com/m-bain/whisperX)** | Toda semana | Transcrição com separação de quem fala. É o que transforma uma call de duas horas em roteiro de entrevista legível. Roda local, sem mandar áudio de cliente para servidor de ninguém. |
| **[mlx-whisper](https://github.com/ml-explore/mlx-examples/tree/main/whisper)** | Quando precisa | Whisper otimizado para o chip da Apple. Muito mais rápido quando não preciso saber quem falou. |
| **[whisper.cpp](https://github.com/ggml-org/whisper.cpp)** | Quando precisa | Versão enxuta, boa para arquivo curto e máquina fraca. |
| **[ffmpeg](https://ffmpeg.org)** | Todo dia | O canivete de mídia. Extrai áudio de vídeo, corta trecho, converte formato, comprime. Quase toda ferramenta desta seção depende dele por baixo. |
| **[yt-dlp](https://github.com/yt-dlp/yt-dlp)** | Toda semana | Baixa vídeo e áudio de plataforma para virar transcrição e estudo de referência. |

```bash
brew install ffmpeg yt-dlp whisper-cpp
pipx install whisperx
pipx install mlx-whisper
```

> **Armadilha que me custou uma tarde:** a diarização (a parte que separa os locutores) não funciona com ffmpeg 8. Precisa de ffmpeg 4 a 7. A solução é instalar a versão fixada em paralelo — `brew install ffmpeg@7` — e apontar o script para ela. Está explicado em [setup-mac-estrategista](https://github.com/ramonniellymorais/setup-mac-estrategista).

O script que eu uso para isso, com a diarização já resolvida, está em [transcrever](https://github.com/ramonniellymorais/transcrever).

---

## 3. Tirar texto de onde ele está preso

| Ferramenta | Uso | O que resolve |
|---|---|---|
| **[Tesseract](https://github.com/tesseract-ocr/tesseract)** | Quando precisa | OCR. Lê texto dentro de imagem: print de conversa, slide fotografado, PDF escaneado, criativo de concorrente. |
| **[Poppler](https://poppler.freedesktop.org)** | Quando precisa | Extrai texto e imagem de PDF, e converte página em PNG. É como eu leio manual de marca e material de cliente que só existe em PDF. |

```bash
brew install tesseract poppler
```

---

## 4. Publicar coisa na internet

Página de captura, calculadora-isca, quiz de diagnóstico, apresentação. A régua técnica caiu tanto que a parte difícil voltou a ser decidir o que dizer.

| Ferramenta | Uso | O que resolve |
|---|---|---|
| **[Vercel CLI](https://vercel.com/docs/cli)** | Toda semana | Coloca site no ar de dentro do terminal, com endereço em segundos. |
| **[GitHub CLI (`gh`)](https://cli.github.com)** | Todo dia | Cria repositório, sobe código, abre pull request sem sair do terminal. Este repositório que você está lendo nasceu com um comando dele. |
| **[Supabase CLI](https://supabase.com/docs/guides/cli)** | Quando precisa | Banco de dados para quando a página precisa guardar lead, resposta de quiz ou histórico. |
| **[Railway CLI](https://docs.railway.com/guides/cli)** | Quando precisa | Hospeda serviço que precisa ficar ligado o tempo todo. |
| **[Deno](https://deno.com)** | Quando precisa | Roda script isolado sem instalar dependência. Bom para tarefa avulsa. |

```bash
brew install gh supabase deno
npm install -g vercel @railway/cli
```

---

## 5. Mover e guardar arquivo

| Ferramenta | Uso | O que resolve |
|---|---|---|
| **[rclone](https://rclone.org)** | Toda semana | Sincroniza pasta local com Google Drive, Dropbox e afins pelo terminal. É como o material de cliente entra na máquina para ser processado em lote. |
| **[SQLite](https://sqlite.org)** | Quando precisa | Banco em um arquivo só. Serve para consultar histórico exportado de aplicativo e organizar planilha grande demais para o Sheets. |
| **[GnuPG](https://gnupg.org)** | Quando precisa | Criptografia. Para quando é preciso guardar ou mandar algo sensível. |

```bash
brew install rclone sqlite gnupg
```

---

## 6. Instalar sem quebrar o Mac

Esta seção parece detalhe e é a que mais evita dor de cabeça. Instalar coisa de Python direto no sistema é como escrever no arquivo original em vez de duplicar antes: um dia dá errado e você não sabe onde foi.

| Ferramenta | Uso | O que resolve |
|---|---|---|
| **[Homebrew](https://brew.sh)** | Base | O instalador de tudo no Mac. Primeira coisa a instalar. |
| **[pipx](https://pipx.pypa.io)** | Base | Instala programa de Python em ambiente isolado. Cada ferramenta na sua caixa, sem uma derrubar a outra. |
| **[uv](https://docs.astral.sh/uv)** | Base | Gerenciador de Python muito rápido. Substitui pip e venv com menos cerimônia. |

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
brew install pipx uv
pipx ensurepath
```

---

## 7. Conectar o Claude ao resto do trabalho

Aqui está o pulo do gato, e é a parte que quase ninguém explica direito.

**MCP** (Model Context Protocol) é o padrão que deixa o Claude conversar com as ferramentas onde o trabalho realmente mora. Sem isso, o assistente vive numa caixa e você fica de copia e cola entre abas. Com isso, ele lê o Notion, abre a planilha, navega no site, consulta o banco.

Os que eu mantenho ligados:

| Conexão | O que destrava |
|---|---|
| **[Notion](https://developers.notion.com/docs/mcp)** | Calendário editorial, banco de ideias, base de referências. O planejamento deixa de ser exportado e passa a ser lido e escrito no lugar onde já vive. |
| **[Google Drive](https://developers.google.com/workspace)** | Transcrição, documento de cliente, planilha de mineração. |
| **[Playwright](https://github.com/microsoft/playwright-mcp)** | Navegador controlado. Serve para abrir página, tirar print, conferir se o site subiu certo. |
| **[GitHub](https://github.com/github/github-mcp-server)** | Repositório, issue, pull request. |
| **[Supabase](https://supabase.com/docs/guides/getting-started/mcp)** | Consulta ao banco sem abrir painel. |

Instalação de um MCP, no formato geral:

```bash
claude mcp add <nome> -- <comando do servidor>
claude mcp list
```

> **MCP não é plugin, e a confusão é comum.** Plugin empacota comandos e agentes prontos dentro do próprio Claude Code. MCP é ponte para um serviço de fora. Um organiza o que ele sabe fazer, o outro amplia onde ele consegue chegar.

---

## O que eu não uso

Vale tanto quanto a lista de cima.

- **Ferramenta que agenda post por mim.** Publicar é o momento em que eu decido se aquilo ainda faz sentido. Automatizei quase tudo em volta e deixei essa decisão de fora de propósito.
- **Gerador de legenda automática de post.** A parte que a máquina faz bem é a que menos importa aqui.
- **Banco de template de copy pronta.** É exatamente o que faz marca virar cópia barata. Se você quiser o caminho contrário, o [checar-copy](https://github.com/ramonniellymorais/checar-copy) reprova as construções que denunciam copy de fórmula.

---

## Continua

- **[setup-mac-estrategista](https://github.com/ramonniellymorais/setup-mac-estrategista)** — instalar tudo isso na ordem certa, do zero
- **[transcrever](https://github.com/ramonniellymorais/transcrever)** — reunião virando roteiro com identificação de quem fala
- **[checar-copy](https://github.com/ramonniellymorais/checar-copy)** — o verificador que reprova copy genérica
- **[radar-de-plataformas](https://github.com/ramonniellymorais/radar-de-plataformas)** — o que Instagram, TikTok, YouTube e LinkedIn confirmaram oficialmente, com fonte e data

---

Feito por **[Ramonnielly Morais](https://ramonniellymorais.com.br)**, criadora do Método ELO Criativo.
Ferramenta é o piso. O que ninguém instala é a sua voz.

Licença [CC BY 4.0](LICENSE) — use, adapte, cite a fonte.
