# BMAD — JORNADA ASSISTIDA PORT ATAQUE I

V1 do projeto de implementação do BMAD para a squad JORNADA ASSISTIDA PORT ATAQUE I.

## Objetivo

Criar um sistema operacional de engenharia baseado em Knowledge Base + skills + human gates,
capaz de padronizar e acelerar Discovery, Story, Refinamento, Desenvolvimento, Testes e Release,
reduzindo concentração de conhecimento no Tech Lead sem retirar dos humanos a responsabilidade
pelas decisões.

## Princípio central

> A IA acelera e padroniza o trabalho; os humanos continuam responsáveis pelas decisões e gates.

## Estrutura

- `knowledge/` — conhecimento persistente da squad.
- `skills/` — futuras competências executáveis do BMAD.
- `workflows/` — fluxos ponta a ponta.
- `templates/` — artefatos e modelos.
- `workspace/` — mapeamento local dos repositórios.
- `examples/` — exemplos futuros e casos de referência.

## Status

V1 = baseline documental + arquitetura das skills. As skills ainda não são consideradas
implementações prontas para execução.

## Próximos passos

1. Revisar KB com o time.
2. Preencher TODOs com dados corporativos.
3. Adicionar repos de referência, desenho de solução e GMUD.
4. Implementar primeiro vertical slice: `context-assembler` → `story-builder`.
5. Evoluir para technical refinement, development, testing e release.
