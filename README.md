# leilaalgarve

Portfolio e blog de Leila Algarve, feito com [Hugo](https://gohugo.io), tema
[PaperMod](https://github.com/adityatelange/hugo-PaperMod) e comentários via
[giscus](https://giscus.app). Publicado no Cloudflare Pages.

## Estrutura

```
archetypes/            modelos para `hugo new` (posts e projetos)
assets/css/extended/   CSS próprio, carregado automaticamente pelo PaperMod
content/
  portfolio/           um projeto por pasta (page bundle: index.md + imagens)
  posts/               um post por pasta (page bundle)
  sobre.md, arquivo.md, busca.md
layouts/_partials/     sobrescritas do tema (giscus, licença, links de projeto)
static/_headers        cabeçalhos HTTP do Cloudflare Pages
themes/PaperMod/       tema (git submodule; não editar)
hugo.yaml              configuração do site
```

## Desenvolvimento local

Requer Hugo **extended** 0.146.0 ou mais recente.

```sh
git clone --recurse-submodules https://github.com/lalgarve/leilaalgarve.git
cd leilaalgarve
hugo server -D          # http://localhost:1313, inclui rascunhos
```

Se o repositório já foi clonado sem o tema: `git submodule update --init --recursive`.

### Novo conteúdo

```sh
hugo new content posts/meu-post/index.md
hugo new content portfolio/meu-projeto/index.md
```

Os arquivos nascem com `draft: true`. Troque para `false` para publicar.

Nos projetos do portfolio, `links` no front matter vira a lista de botões no fim da página,
e `weight` define a ordem na listagem.

### Atualizar o PaperMod

```sh
git submodule update --remote --merge themes/PaperMod
```

## Comentários (giscus)

1. Deixe o repositório **público** e ative **Discussions** (Settings → General → Features).
2. Crie uma categoria de discussão chamada `Comentários`, do tipo *Announcement*, para que
   só o giscus crie discussões nela.
3. Instale o app giscus: <https://github.com/apps/giscus>.
4. Em <https://giscus.app>, informe `lalgarve/leilaalgarve`, escolha a categoria e copie
   `data-repo-id` e `data-category-id` para `params.giscus.repoId` e
   `params.giscus.categoryId` no `hugo.yaml`.

Enquanto os dois IDs estiverem vazios, os comentários não aparecem. Para desligar em uma
página, use `comments: false` no front matter. O tema do giscus acompanha o botão
claro/escuro do site.

## Deploy no Cloudflare Pages

Em *Workers & Pages → Create → Pages → Connect to Git*, escolha este repositório e use:

| Campo                  | Valor                  |
| ---------------------- | ---------------------- |
| Framework preset       | Hugo                   |
| Build command          | `hugo --gc --minify`   |
| Build output directory | `public`               |
| Variável de ambiente   | `HUGO_VERSION=0.166.0` |

O Cloudflare Pages baixa o submodule do tema automaticamente. Sem `HUGO_VERSION`, ele usa
uma versão antiga do Hugo, e o PaperMod não compila.

Depois de configurar um domínio próprio, atualize `baseURL` no `hugo.yaml`.

## Licenças

- **Conteúdo** (textos, imagens e demais arquivos em `content/` e `static/`):
  [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.pt-br). Veja
  [`LICENSE`](LICENSE).
- **Código** (templates, CSS, configuração e scripts): [MIT](LICENSE-MIT).
- **Tema PaperMod**: MIT, pelos seus autores. Veja `themes/PaperMod/LICENSE`.
