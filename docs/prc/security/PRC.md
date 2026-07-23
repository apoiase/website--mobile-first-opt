# PRC — Security (scanning, higiene de secrets, acesso)

Status em 2026-07-18. Validadores: SEC + SRE.

## Checklist

- [x] **SEC1** — Secret scanning no PR (`gitleaks:v8.30.1`, criado neste rollout)
- [x] **SEC2** — SAST no PR (Semgrep `1.169.0`, `p/typescript` + `p/security-audit`)
- [x] **SEC3** — SCA no PR (Trivy fs `0.72.0`, `HIGH,CRITICAL`, consultivo)
- [ ] **SEC4 (achado pré-existente)** — `plasmic-init.ts` versiona um **Plasmic project API
  token** hardcoded no código-fonte (par do project id `3f38a6Y6BqwkUbTMSSJTn1`). Pelo padrão
  documentado do `@plasmicapp/loader-nextjs`, este é o token de **loader** do projeto —
  destinado a ser embutido em código client-side (leitura/renderização de conteúdo publicado,
  análogo a uma chave publicável), não uma credencial administrativa da conta Plasmic. Ainda
  assim é um segredo versionado: **não rotacionado nesta sessão** (regra "mapear antes de
  remediar") — confirmar com o time que é de fato um loader token (não um token de API completo
  com permissão de escrita) antes de decidir se vale mover para env var/GitHub Secret
- [ ] **SEC5** — Renovate/Dependabot: recomendação aberta, não configurado
- [ ] **SEC6** — Dependências antigas (Next.js 12.1.6, React 18.2.0 de 2026) sem atualização
  automatizada

## Exceções aceitas

| Item | Justificativa | Data |
|---|---|---|
| — | — | — |
