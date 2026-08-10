# Crate — app pessoal de álbuns

## Antes de usar
1. Abra `index.html` num editor de texto.
2. Ache a linha `const SPOTIFY_CLIENT_SECRET = 'COLOQUE_SEU_CLIENT_SECRET_AQUI';`
3. Troque pelo Client Secret do seu app no [Spotify Developer Dashboard](https://developer.spotify.com/dashboard).
4. Salve e abra o `index.html` no navegador (ou publique no GitHub Pages).

⚠️ **Atenção:** como é um app estático (sem servidor por trás), o Client Secret fica visível
pra qualquer um que abrir o código-fonte da página no navegador ou olhar o repositório, caso
o publique no GitHub Pages com repositório público. Para uso pessoal de baixo volume, o risco
prático é baixo — mas não é o mesmo padrão de segurança de um app com backend próprio. Se um dia
isso incomodar, dá pra migrar para o fluxo de login com Spotify (Authorization Code + PKCE) que
não expõe o secret, ou colocar essa troca de token atrás de uma function serverless.

## Publicar no GitHub Pages (mesmo fluxo do app de filmes/séries)
1. Crie um repositório novo (pode ser público) e suba estes arquivos: `index.html`, `manifest.json`, `sw.js`, `icon-192.png`, `icon-512.png`.
2. Nas configurações do repositório, ative o GitHub Pages apontando para a branch principal.
3. Acesse a URL gerada — no celular, use "Adicionar à tela inicial" pra instalar como app.

## O que já funciona (v1)
- Busca de álbuns e artistas via API do Spotify (Client Credentials Flow — sem login)
- Ficha do álbum com faixas, ano, e botão pra ir até o artista
- Página do artista com discografia cronológica: álbuns de estúdio primeiro (mais antigo → mais novo),
  deluxes/lives/compilações numa seção separada abaixo
- Criar listas com nome livre e adicionar álbuns a elas (direto no card ou na ficha do álbum)
- Tudo salvo em localStorage — sem conta, sem sync entre dispositivos, uso individual no aparelho

## Limitações conhecidas dessa v1
- A separação "discografia original vs. deluxe/outros" é feita por palavras-chave no nome do álbum
  (deluxe, remaster, live, edition, etc.) — não é 100% precisa. A correção via Wikipedia fica pra v2.
- Sem sync entre dispositivos (fica só no navegador onde foi usado).
- A API do Spotify não retorna mais "lançamentos recentes" nem "recomendações" (endpoints
  descontinuados pela própria Spotify) — por isso a Home não tem essas seções.
