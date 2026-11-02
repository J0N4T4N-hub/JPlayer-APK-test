# JPlayer

Player de música offline (PWA) com IA.

## Publicar no GitHub Pages
1. Crie um repositório no GitHub (ex.: `jplayer`).
2. Envie todos os arquivos desta pasta para a raiz do repositório.
3. Em **Settings → Pages**: Source = *Deploy from a branch*, Branch = `main` / `(root)` → Save.
4. Aguarde 1–2 min e abra `https://SEU-USUARIO.github.io/jplayer/` no Chrome do celular.
5. Menu ⋮ → **Instalar app** / **Adicionar à tela inicial**.

## Transformar em app Android (APK/AAB)
1. Com o site no ar, abra https://www.pwabuilder.com e cole a URL do GitHub Pages.
2. Clique em **Package for stores → Android** e baixe o pacote.
3. Instale o `.apk` no celular (ou use o `.aab` na Play Store).

## Atualizar
Ao mudar o app, aumente o número em `CACHE` no `service-worker.js` (ex.: `jplayer-v2`).

## IA do chat
- **Fila, não playlist:** o que você pede para tocar vai só para a fila. A IA **nunca cria playlist sozinha**: só cria quando você pedir (ex.: "cria uma playlist de rock"). Essa regra também é travada no código, não só na conversa.
- Nome repetido não substitui nada: a nova vira "Nome (2)".
- Pedidos que ela entende: tocar (a fila vira só o pedido), "coloca X na fila" (sem interromper), tocar uma playlist sua, adicionar em playlist existente, salvar a fila como playlist, pular, voltar, pausar, embaralhar, limpar fila, favoritar e mudar o volume.
- Ela sabe o que está tocando, a fila, suas favoritas, as mais tocadas, as recentes e as suas playlists.
- "Apaga as playlists automáticas" remove as que a versão antiga criou sozinha (nome termina com data, ex.: "Para hoje · 01/11"), sempre pedindo confirmação.
- A cada mensagem, a IA recebe o catálogo **atualizado** da biblioteca (títulos, artistas e estilos). Música nova importada já é conhecida na próxima mensagem.
- Ao adicionar músicas, a IA avisa no chat e classifica o estilo delas (com internet).
- Biblioteca muito grande: a IA vê os artistas principais + as músicas mais relevantes ao pedido.
- Sem internet (ou com a opção "só no Wi-Fi" ligada no 4G/5G), o chat usa o modo local: estilos, climas e artistas.

## Letras automáticas
- Toda música importada tem a letra procurada e salva sozinha (LRCLIB, precisa de internet). Se a música já traz letra no arquivo, ela é mantida.
- Ao abrir o app, as músicas que ainda estão sem letra entram na fila. Sem internet, a busca continua quando a conexão voltar.
- Letra não encontrada é tentada de novo depois de 7 dias; o botão "Buscar letra online" tenta na hora.
- A opção "só no Wi-Fi" também vale para a busca de letras.
- A letra aparece num cartão colorido embaixo do player (botão "Letra"). Quando existe versão sincronizada, a linha atual acompanha a música, e tocar numa linha pula para ela.

## Jplay Wrapped e Jplay Guess (Ajustes)
- Wrapped: o app registra cada reprodução (a partir de 15 s ouvidos) no próprio aparelho. As estatísticas são calculadas só com esse histórico real, por mês ou por ano, em formato de stories, e cada card pode ser compartilhado como imagem.
- Guess: o jogo usa só os arquivos da sua biblioteca, tocados no próprio aparelho. Modos: diário, Endless, Artist e Hardcore, com recorde, histórico e ranking pessoal. Os resultados também aparecem no Wrapped.

## Abertura
- Ao abrir o app, a imagem do ícone aparece quebrada e se reconstrói em cerca de 2 s. Some sozinha, não bloqueia o app e é desativada quando o aparelho está com "reduzir movimento".
