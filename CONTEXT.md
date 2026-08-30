# Contexto consolidado — Implementação do BMAD

## 1. Como chegamos até aqui

Este documento consolida as decisões e descobertas realizadas durante o levantamento inicial
do BMAD da JORNADA ASSISTIDA PORT ATAQUE I. Ele existe para permitir continuidade em sessões futuras
sem precisar reconstruir todo o contexto.

## 2. Squad

**Nome:** JORNADA ASSISTIDA PORT ATAQUE I

**Missão:** manter e aprimorar a rota assistida de contratação de portabilidade de consignado
para servidores públicos, trazendo a melhor experiência para os gerentes de agência e atendendo
às regras do produto.

**Usuário principal:** gerente de agência.

**Beneficiário final:** servidor público que deseja portar contratos de consignado de outros bancos.

## 3. Boundary

A jornada começa quando o gerente acessa a rota de contratação dentro do 360i e termina
na geração/encerramento do escopo da jornada conforme o fluxo de formalização.

A evolução da proposta após a geração é responsabilidade dos times de pós-jornada.

A squad consome, mas não é owner, de contextos como oferta backend, parametrização de convênios,
convênio colaborador, precificação, análise de crédito, averbação, processadoras, custódia,
seguros, Open Finance e máquina de estado, salvo os componentes explicitamente classificados
como shared/owned.

### Owned — Canal

- 360i → Consumer
- Jornada Web → Owned
- Microfrontends / Building Blocks → Owned
- BFFs → Owned
- Gateways → Owned

### Shared — Backend

- Simulação
- Consentimento
- Dívidas
- Vendas
- Gestão de Clientes (NR8)
- Mínimos e Máximos
- Elegibilidade
- Saldo Remanescente
- Gestão de Autorizações

A squad é guardiã técnica da API de Gestão de Autorizações, embora ela seja compartilhada entre
canais.

### Consumer — Contextos externos

- Oferta
- Parametrização de convênios
- Convênio Colab
- Precificação
- Análise de crédito
- Averbação
- Processadoras
- Custódia
- Seguros
- Open Finance
- Máquina de estado

### Out of scope

- Canais legados
- Jornadas legadas
- Pós-jornada da proposta

Ownership de uma peça compartilhada é previamente definido. Quando uma necessidade pertence ao
time owner, normalmente ele desenvolve. Quando a necessidade pertence a outro time, esse time
pode desenvolver com apoio do owner, que deve proteger o contexto contra efeitos colaterais.

## 4. Pessoas e responsabilidades

### Product Manager

Formalmente responde por:

- objetivo do produto;
- escopo funcional;
- priorização;
- regras de negócio;
- critérios de aceite;
- aceite da entrega.

### Product Designer

Participa principalmente de discovery/inception, definindo experiência, comportamento de telas
e uso do iDS. Pode voltar durante desenvolvimento para dúvidas de Figma e CX review.

### Tech Lead

Responsável por decisões técnicas, arquitetura do dia a dia, capacity, delegação, refinamento
técnico, code review, apoio a testes/release e conhecimento transversal.

Um objetivo central do BMAD é reduzir a concentração de conhecimento no Tech Lead.

### Desenvolvedores

Refinam tecnicamente, implementam, escrevem testes, realizam self-review e participam dos PRs.
São engenheiros de software de ponta a ponta, incluindo código, infra, SRE e qualidade.

### Squads parceiras

Participam de inceptions maiores; SMEs ajudam no acompanhamento de dependências. Demandas menores
são alinhadas entre PMs/Tech Leads.

## 5. Domínio de negócio

### Portabilidade

Portabilidade é trazer um contrato de empréstimo de outro banco para o banco da squad.

Motivações incluem relacionamento, redução de taxa/parcela, carência e/ou troco.

A operação é regulamentada pela Nuclea e envolve período para tentativa de retenção pelo banco origem.

### Jornada assistida

O gerente executa a jornada em nome do cliente, orientando-o por comunicação presencial/remota.
A formalização, porém, deve ser realizada pelo próprio cliente.

Formas de formalização na jornada:

- cartão e senha;
- biometria e senha.

Formalização remota ocorre no SuperApp e pertence à jornada digital depois que o cliente opta por ela.

### Modalidades

- **Modalidade 3:** portabilidade pura, sem troco.
- **Modalidade 5:** refinanciamento de portabilidade, com troco. Gera duas operações/propostas
  dependentes: modalidade 3 primeiro; modalidade 5 somente após conclusão da portabilidade.
- **Modalidade 8:** retenção de portabilidade; não faz parte da atuação da jornada.

### Conceitos importantes

- **Saldo devedor:** valor necessário para liquidar o contrato hoje, não a soma das parcelas futuras.
- **Margem:** capacidade mensal disponível para comprometimento consignável; em geral próxima de
  percentual da renda, variando por convênio.
- **Convênio:** órgão/empregador público do cliente.
- **Processadora:** entidade que atende diversos convênios e gerencia folha/repasse.
- **Averbação:** comprar a dívida/incluir o contrato como ativo sob responsabilidade do banco.
- **Desaverbação:** processo contrário.
- **Troco:** valor adicional disponibilizado no refinanciamento de portabilidade.
- **Prazo:** tempo durante o qual o cliente pagará o contrato.
- **Oferta:** representa o máximo que pode ser oferecido dentro das regras.
- **Simulação:** trabalha em um range entre mínimo e máximo e serve de base para a oferta.
- **Combo de ofertas:** agrega simulações de produtos associados; a portabilidade é a base e o
  produto associado pode ser recusado pelo cliente.

### Regras relevantes

- Taxa da portabilidade não pode ser maior que a taxa do contrato origem.
- Sem troco, o prazo deve acompanhar o prazo remanescente do contrato origem e não deve diminuir.
- Com troco, entram margem, perfil de crédito e regras do convênio.
- Oferta é apresentada uma vez e usa os valores máximos possíveis.
- Modalidade 5 pode ser cancelada antes do início se o recálculo indicar que o cliente não é mais
  elegível para o troco.
- Após averbação, não há cancelamento de proposta; passa a ser outro fluxo de contrato.
- Contrato liquidado não é elegível.
- Atualmente a squad não porta contratos de cooperativas.
- Elegibilidade considera regras externas, internas, perfil, vínculo, idade, convênio, risco,
  rentabilidade e decisão de produto.
- Convênios podem impor particularidades como consentimento, anuência de averbação e token.

## 6. Fluxo da jornada

iClientes (Microsoft Dynamics)
→ menu Crédito Consignado → Portar Contratos
→ 360i
→ Jornada JU9.

O iClientes identifica o cliente por CPF/agência/conta, mas a jornada recebe identificadores:
`idCliente` e `idConta`, evitando trafegar os dados sensíveis diretamente.

Na jornada, o contrato pode vir de Open Finance ou de digitação manual baseada na DED.

A base de dívidas usa como identificador o número do contrato concatenado ao código do banco.
Um novo input do mesmo contrato atualiza seus dados. Dados obrigatórios:

- número do contrato;
- quantidade total de parcelas;
- parcelas pagas;
- taxa;
- banco origem;
- saldo devedor;
- valor da parcela.

Open Finance é facilitador. O gerente deve confirmar os dados com o cliente. Se houver inconsistência,
o workaround é digitar manualmente os dados corretos.

## 7. Arquitetura

### Contas/contextos

- Jornada: conta AWS **JU9**.
- Building Blocks: conta AWS **KF6**.

A jornada JU9 hospeda Building Blocks. Cada Building Block é composto por um microfrontend e um BFF.

Building Blocks isolam pequenas etapas, como consentimento, oferta e resumo.

Building Blocks não são as APIs backend compartilhadas. Eles pertencem ao domínio dos canais.

A jornada funciona como chassi e recebe eventos dos Building Blocks. O Building Block informa quando
terminou; a jornada aplica a regra de negócio e decide qual bloco exibir em seguida.

**Princípio:** regras de negócio específicas de modalidade/segmento devem permanecer na jornada
sempre que possível; Building Blocks devem ser agnósticos.

### BFF

BFFs:

- Kotlin;
- Java 17+ (alguns 21);
- Spring Boot;
- Maven;
- REST;
- AWS ECS;
- API Gateway;
- Datadog.

BFFs usam screaming architecture, com `controller` e `useCase`. Componentes compartilháveis ficam
em `service` fora da camada screaming.

BFFs chamam APIs backend e adaptam contratos para o frontend.

### Frontend

- Angular.
- Componentes do iDS devem ser utilizados; não se deve criar botões/labels manualmente fora do
  padrão.

### Caronte

A comunicação frontend → BFF passa pelo proxy reverso Caronte. Ele criptografa chamadas, gera um
REL temporário e evita que o frontend conheça diretamente o DNS do BFF.

### APIs

REST.

Headers importantes:

- `x-itau-correlationID`
- `x-itau-jornadaID`

Retornos 2xx usam `{ "data": {} }`.
Retornos 4xx/5xx geralmente usam `{ "erros": [] }`.

## 8. Engenharia

### GitHub

- GitHub é usado para código, PRs e Actions.
- Branches de trabalho usam `feature/`.
- PR para `develop` exige ao menos um approve por convenção.
- CODEOWNERS existe em alguns repos.
- Após merge em develop, deploy para DEV é automático.
- Depois de DEV, PR para release é criado automaticamente.
- Merge de release promove para HOMOL.
- Depois de HOMOL, PR para main.
- GMUD aprovada é necessária antes do deploy em PROD.
- Action integra com ServiceNow para validar aprovação da GMUD.

### CI/CD

Gates conhecidos:

- Sonar;
- SECaaS;
- Veracode;
- TAAC;
- lint;
- segurança.

Sonar roda após deploy e usa quality gate de 90%; a squad mira 95% internamente.

TAAC roda após deploy no ambiente correspondente.

Produção é validada essencialmente de forma manual. Testes sintéticos/carga fria existem em poucos
repos, mas não são regra.

### Terraform / HN8

Toda infraestrutura AWS deve ser provisionada com Terraform.

HN8 fornece módulos/templates para infraestrutura AWS.

IaC fica no mesmo repo da aplicação quando pertence àquela aplicação.

Ambientes:

- dev;
- homol;
- prod.

Configuração comum pode estar em `main.tf`/`variables.tf`; particularidades ficam em `inventories`
por ambiente.

Mudanças de infra seguem o mesmo PR/approval da aplicação.

## 9. Qualidade

### Unitários

- Backend: testes unitários; cobertura mínima desejada de 95%.
- Frontend: Jest.
- Sonar valida cobertura.

### Integrados/automatizados

- Backend: integração/TAAC.
- Frontend: Cypress.
- Integrados devem estar segregados dos unitários e corretamente configurados no `pom`/testspecs.

### Testes funcionais

Critérios de aceite são a referência principal e devem ser funcionais/observáveis.

Preferir DADO/QUANDO/ENTÃO.

Evitar critérios técnicos como nomes de métodos, arquivos ou componentes.

A skill de teste deve primeiro verificar cobertura automatizada e só depois criar testes manuais para
lacunas ou comportamentos que realmente demandem validação humana.

Regressão é definida conforme impacto, especialmente quando componentes compartilhados são alterados.

### IUQuali e evidências

Cenários no IUQuali usam DADO/QUANDO/ENTÃO.

Ao finalizar uma execução, o IUQuali gera um código que é associado à GMUD.

Evidências preferenciais:

- vídeos com OBS Studio;
- armazenados no SharePoint;
- link compartilhável;
- arquivo `.txt` associado ao teste no IUQuali.

Para BFFs/serviços testados via Insomnia/Bruno, prints podem ser suficientes em casos adequados.

### Conhecimento de teste

Procedimentos de massa, by-pass e troubleshooting hoje estão parcialmente concentrados no Tech Lead.
O BMAD deve capturar esse conhecimento e reutilizá-lo em histórias futuras.

## 10. Release

GMUD é gerada por repositório. Uma história que altera três repos pode resultar em três GMUDs.

Playbook deve conter, no mínimo:

- número GMUD;
- data;
- janela;
- alterações;
- responsáveis;
- validação;
- dashboard Datadog;
- rollback;
- critérios de rollback.

Hoje a IA já gera o playbook a partir de template HTML + história + histórico do desenvolvimento.

Pós-deploy ocorre call gravada com PM, Tech Lead, dev e Group Tech Manager I. A sessão cobre esteira,
playbook e validação funcional. O vídeo/link é evidenciado na GMUD.

## 11. Fluxo de IA atualmente desejado

1. Ler história.
2. Ler Knowledge Base.
3. Identificar componentes afetados.
4. Ler padrões do repositório quando necessário.
5. Fazer plano de implementação.
6. Validar plano.
7. Implementar.
8. Criar testes.
9. Executar testes.
10. Fazer self-review.
11. Code review do solicitante.
12. Criar PR quando o solicitante informar que está tudo certo.

## 12. Filosofia BMAD

A IA deve acelerar e padronizar, não substituir ownership humano.

Human gates:

- PM: objetivo, escopo, regras, critérios e aceite.
- Tech Lead/Arquitetura: decisões arquiteturais.
- Dev/Tech Lead: aprovação técnica do plano quando necessário.
- Reviewer: code review.
- Release/GMUD: autorização de produção.
- PM + Dev + Tech Lead + demais responsáveis: validação produtiva.

A IA não deve criar repos. O responsável fornece os repos de atuação.

## 13. Próximo estado desejado

Transformar este baseline em um sistema operacional de engenharia:

Demanda
→ Context Assembly
→ Discovery
→ Story Builder
→ Technical Refinement
→ Development
→ Testing
→ Code Review
→ Release
→ Production Validation
→ Knowledge Capture
→ Knowledge Base.

## 14. TODOs prioritários

- Repos reais e repos de referência.
- Desenho de solução da geração da oferta.
- Desenho/artefato real de inception/showcase.
- Exemplo real de GMUD.
- Template HTML do playbook.
- Stack/padrões detalhados de Angular.
- Repo de referência de BFF.
- Repo de referência de API produto.
- Repo de referência de testes backend.
- Collection Bruno.
- Link/template SharePoint para evidências.
- Procedimentos de by-pass.
- Troubleshooting de testes.
- Troubleshooting de produção.
- Definition of Done oficial.
- Mecanismo de workspace/repos locais.
- Regras para commits/alterações automáticas em repos auxiliares.
- Integrações corporativas disponíveis para ServiceNow, GitHub, IUQuali, SharePoint e Datadog.
