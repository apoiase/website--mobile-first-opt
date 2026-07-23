# Production Readiness Checklist (PRC)

Checklists de prontidão por escopo deste repo, com o **status atual honesto**. Adaptado do
modelo "Production Readiness Checklist — Nova APOIA.se" (tiers Copper/Silver/Gold), colapsados
numa única coluna por ser um repo brownfield sem tiers de promoção formais.

## Convenções

- Um escopo por pasta: `docs/prc/<escopo>/PRC.md`
- IDs de item: `<PREFIXO><n>` — estáveis, referenciáveis em PRs e no Jira
- Status: `[x]` feito · `[ ]` gap
- Exceções aceitas vivem na seção "Exceções aceitas" de cada escopo
- Validadores: DEV (time dev) · SRE (infra) · SEC (segurança)

## Escopos

| Escopo | Cobre |
|---|---|
| [`github/`](github/PRC.md) | Config do repo, Actions, fluxo de PR, quality gates |
| [`aws/`](aws/PRC.md) | Runtime (GitHub Pages, não AWS) |
| [`observability/`](observability/PRC.md) | Logs, erros, alertas, métricas |
| [`security/`](security/PRC.md) | Scanning, higiene de secrets, acesso |

## Nota de escopo (NA-598)

Repo mapeado do zero. É um app-host Plasmic sem lógica de negócio própria — o conteúdo real
vive no Plasmic Studio, fora do controle de versão.
