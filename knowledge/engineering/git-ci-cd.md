# Git & CI/CD

- GitHub para código, PRs e Actions.
- Branches de trabalho usam `feature/`.
- PR para `develop`: ao menos um approve por convenção.
- CODEOWNERS existe em alguns repos.
- Merge em develop → deploy DEV.
- Após DEV → PR release.
- Merge release → deploy HOMOL.
- Após HOMOL → PR main.
- GMUD deve estar aprovada antes do deploy PROD.
- Action integra com ServiceNow.

## Gates

- Sonar
- SECaaS
- Veracode
- TAAC
- lint
- segurança

Sonar ocorre após deploy e possui quality gate de 90%; squad mira 95%.

TAAC roda no ambiente após deploy.

Produção é manualmente validada como regra geral.
