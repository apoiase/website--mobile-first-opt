# PRC — GitHub (repo, Actions, fluxo de PR)

Status em 2026-07-18. Validador: SRE.

## Checklist

- [x] **GH1** — Quality gates de PR via Actions (`.github/workflows/quality-gates.yml`, criado
  neste rollout — não conflita com `plasmic.yml`/`plasmic-push.yml` existentes): gitleaks +
  Semgrep (`p/typescript` + `p/security-audit`) + Trivy fs, todos consultivos
  (`continue-on-error: true`)
- [x] **GH2** — Pipes/imagens de terceiros pinados em versão exata nos gates novos
- [ ] **GH3** — `plasmic.yml`/`plasmic-push.yml` usam `plasmicapp/plasmic-action@master` e
  `JamesIves/github-pages-deploy-action@4.1.0` sem SHA pin (branch `master` é *moving target*) —
  considerar pin por SHA ou tag imutável
- [ ] **GH4** — Sem template de PR
- [ ] **GH5** — Sem step de review agentic no PR — requer secret de API do provedor de LLM
- [ ] **GH6** — Branch protection na `main`: não verificável só pelo código
- [ ] **GH7** — Renovate/Dependabot: recomendação aberta, não configurado

## Exceções aceitas

| Item | Justificativa | Data |
|---|---|---|
| — | — | — |
