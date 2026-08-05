# website--mobile-first-opt

App-host Next.js gerado por `create-plasmic-app`, usado para publicar o projeto **Plasmic**
"Copy of apoiase--home" (visual builder no-code). O conteúdo de página real não vive neste repo
— vive no Plasmic Studio remoto; o repo é só o esqueleto de integração (catch-all router, host
page) e os workflows que sincronizam a partir do Plasmic e publicam em GitHub Pages.

## Comandos

```bash
yarn install
yarn dev      # next dev
yarn build    # next build
yarn start    # next start
yarn lint     # next lint (eslint-config-next)
```

## Deploy

Dois workflows GitHub Actions, ambos publicando em **GitHub Pages** (branch `gh-pages`), não em
infra AWS da Apoia.se:
- `.github/workflows/plasmic.yml` — disparado por `repository_dispatch` do próprio Plasmic
  Studio quando alguém publica uma mudança lá: inicializa/sincroniza o código gerado, builda e
  publica, abrindo PR se necessário.
- `.github/workflows/plasmic-push.yml` — build+deploy em todo push na `main`, fallback do fluxo
  acima.

## Arquitetura

- `plasmic-init.ts` — inicializa o `PlasmicLoader` com o project id do Plasmic (`apoiase--home`)
  e um **project API token embutido no código-fonte** (ver Production Readiness / SEC abaixo).
- `pages/[[...catchall]].tsx` — único router de fato: para qualquer path, busca os dados da
  página publicada no Plasmic (`PLASMIC.maybeFetchComponentData`) e renderiza via
  `PlasmicComponent`; 404 se não houver match. ISR com `revalidate: 60`.
- `pages/plasmic-host.tsx` — endpoint `/plasmic-host` usado pelo Plasmic Studio como iframe de
  edição visual ao vivo (`PlasmicCanvasHost`).
- `pages/api/hello.ts`, `styles/Home.module.css` — resíduos do boilerplate `create-next-app`,
  nunca customizados nem referenciados por página real (confirma que não há componentes React
  desenvolvidos localmente — tudo é editado no Plasmic Studio).

## Contexto de domínio

Sem contexto de domínio Apoia.se mapeado no código (nenhuma referência a Fazedor/Apoiador/
Repasse) — a lógica de conteúdo/negócio, se houver, vive inteiramente no projeto Plasmic
"Copy of apoiase--home", fora deste repositório. Ver `apoiase-context-layer` para confirmar
propósito e uso ativo.

## Convenções

- Commits: mensagens automáticas do bot de sync do Plasmic (`[plasmic] Sync project ...`) +
  commits manuais de setup de workflow.
- Branches: durante o rollout NA-598, `big-picture/NA-598-*`. Deploy real é via `main`.
- Não editar manualmente conteúdo gerado pelo Plasmic — mudanças de página são feitas no
  Plasmic Studio e sincronizadas via `plasmic.yml`.

## Production Readiness

Checklists por escopo em `docs/prc/`. Achado principal: `plasmic-init.ts` versiona um Plasmic
project API token no código — típico de token de loader/publicação (padrão do Plasmic,
equivalente a uma chave publicável client-side), mas registrado como achado de segurança sem
rotação às cegas (ver `docs/prc/security/PRC.md`).

## Knowledge graph

- `graphify-out/graph.html` (interativo) · `graphify-out/GRAPH_REPORT.md` (10 communities)
- `.understand-anything/knowledge-graph.json` (13 nós, 5 layers, tour de 5 passos)


<!-- codegraph:start -->
## CodeGraph

Este repositório tem índice CodeGraph versionado em `.codegraph/codegraph.db`.
Use-o ANTES de `grep`/`find` ou de abrir arquivos quando precisar entender ou
localizar código:

- **MCP** (quando disponível): `codegraph_explore` responde a maior parte das
  perguntas sobre código numa chamada só — devolve o fonte verbatim dos símbolos
  relevantes e os call paths entre eles, incluindo os saltos de dispatch dinâmico
  que o `grep` não acompanha. Cite um arquivo ou símbolo na query para ler o
  fonte atual numerado por linha.
- **Shell** (sempre funciona): `codegraph explore "<símbolos ou pergunta>"`.

O índice acompanha o repositório, então um clone novo já consulta o grafo sem
precisar rodar nada antes. Ele reflete o commit em que foi gerado: depois de
mudar código, `codegraph sync .` atualiza o índice local e `codegraph index .`
reconstrói do zero. Regerar o `.db` versionado é opcional — vale a pena junto de
mudanças estruturais, não é pré-requisito para trabalhar aqui.
<!-- codegraph:end -->
