# Testing & Quality

## Unitários

Backend e frontend devem possuir testes unitários.

Frontend: Jest.

Cobertura desejada: mínimo de 95% no geral.

Sonar valida cobertura.

## Integração / automação

Backend: testes integrados + TAAC.

Frontend: Cypress.

Integrados devem estar segregados dos unitários e corretamente mapeados em `pom`/testspecs.

## Funcional

Critérios de aceite devem ser explicitamente testados.

Critérios devem ser observáveis e não técnicos.

Usar DADO/QUANDO/ENTÃO.

A skill de testes deve:

1. Ler critérios.
2. Mapear cobertura automatizada.
3. Identificar lacunas.
4. Criar testes manuais somente quando necessários.
5. Gerar cenários palpáveis.
6. Indicar dados/by-pass necessários.
7. Preparar evidências.

## Regressão

Decidir conforme impacto, especialmente componentes compartilhados.

## Responsabilidade

Não existe QA dedicado. A organização de quem testa pode variar conforme time.

[TODO — definir Definition of Done.]
