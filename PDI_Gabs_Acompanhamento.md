# PDI — Gabs
**Cargo atual:** Engenheiro de Software Pleno / Tech Lead  
**Baseline:** Setembro/2026  
**Objetivo principal:** evolução para Engenheiro de Software Senior

> **Princípio do PDI:** usar este documento como artefato vivo. O foco é registrar evolução e evidências reais, não apenas atividades realizadas. O documento deve ser revisado com o coordenador periodicamente.

---

## 1. Objetivos de carreira

### Curto prazo — Senior
**Meta:** estar pronto para atuar como Senior em até **4 meses (final de dezembro/2026)**, buscando concretizar a evolução de nível em até **6 meses (final de março/2027)**.

A prontidão será avaliada pela combinação de:
- profundidade técnica;
- liderança escalável;
- comunicação e influência;
- evidências concretas de atuação compatível com o próximo nível.

### Médio prazo — Backend
**Horizonte:** ~1,5–2 anos.

Buscar atuação predominantemente backend, inicialmente como Team Member, aprofundando engenharia backend e arquitetura e, posteriormente, avaliando o retorno a uma posição de Tech Lead.

> Direção de carreira, não compromisso rígido. Revisar conforme oportunidades e contexto.

### Longo prazo — Experiência internacional
**Horizonte:** ~4 anos.

Realizar uma experiência internacional. A duração e o objetivo dependerão do contexto pessoal e profissional no momento:
- intercâmbio de aproximadamente 1,5 mês, com foco em imersão cultural; ou
- experiência mais longa, potencialmente associada a trabalho presencial em tecnologia no exterior.

---

# 2. Baseline

## Trajetória
- **2016–2020:** formação em tecnologia, lógica de programação, C#, bancos, web, redes e inglês.
- **2018–2020:** uso profissional diário de inglês em comunicação internacional, além de desenvolvimento de senso crítico, análise de casos e gestão de situações de conflito.
- **2021–2024:** experiência profissional em Java, com Spring, Hibernate, Struts/JSP, REST/SOAP, mensageria, integração, PostgreSQL, Git/Gerrit, Jenkins, observabilidade, testes e Agile. Forte evolução em domínio de produto e negócio.
- **2024–2026:** empresa atual; expansão para Kotlin, GitHub, Angular, testes frontend, AWS, Terraform e visão E2E. Evolução para Tech Lead interino e posteriormente oficial.

## Pontos fortes
- Engenharia de software e backend.
- Forte domínio de produto e regras de negócio.
- Capacidade de aprender rapidamente novos contextos.
- Liderança técnica já exercida na prática.
- Visão E2E do produto.
- Inglês fluente.
- Boa comunicação e liderança dentro da Squad.

## Principais oportunidades
- Autonomia do time e distribuição de conhecimento.
- Comunicação/exposição em discussões estratégicas cross-team.
- Arquitetura distribuída e orientada a eventos.
- Fundamentos de AWS: IAM, roles/policies e networking.
- NoSQL/DynamoDB e trade-offs de persistência.

---

# 3. Pilares do ciclo

## Pilar 1 — Profundidade técnica

### Objetivo
Aumentar a capacidade de projetar, avaliar e discutir soluções backend distribuídas e cloud-native.

### Focos
**Arquitetura distribuída**
- eventos e mensageria;
- síncrono vs. assíncrono;
- Kafka, SQS, SNS e Kinesis;
- retry, DLQ e idempotência;
- ordenação, concorrência e consistência eventual;
- resiliência.

**Cloud / Security**
- IAM;
- Roles e Policies;
- trust relationships;
- autenticação/autorização;
- least privilege.

**Networking**
- VPC;
- subnets;
- route tables;
- Security Groups;
- Load Balancers;
- exposição pública/privada;
- fluxo de comunicação entre componentes.

**Persistência**
- SQL vs. NoSQL;
- DynamoDB;
- access patterns;
- particionamento;
- consistência e escalabilidade.

### Evidência de conclusão
Não considerar “curso concluído” como evidência suficiente. Buscar aplicação em problemas reais:
- desenho de solução;
- ADR/RFC;
- decisão arquitetural;
- implementação;
- explicação de trade-offs;
- participação em discussões técnicas.

### Checkpoint
**Até dezembro/2026:** conseguir analisar e discutir uma solução backend/cloud considerando comunicação, persistência, segurança, rede, resiliência e trade-offs.

---

## Pilar 2 — Autonomia e escala da liderança

### Objetivo
Reduzir a concentração de conhecimento e decisões no Tech Lead e aumentar a autonomia da Squad.

### Marco 1 — Documentação
**Prazo: final de outubro/2026**

Criar documentação centralizada e utilizável contendo:
- visão do produto;
- arquitetura;
- componentes;
- processos;
- testes;
- deploy;
- troubleshooting/runbooks;
- observabilidade;
- dependências;
- responsabilidades;
- decisões recorrentes;
- conhecimento atualmente concentrado no TL.

**Critério adicional:** orientar o time a consultar a documentação antes de escalar dúvidas recorrentes.

### Marco 2 — Novos Team Members
**Prazo: final de novembro/2026**

Os dois novos integrantes devem:
- conhecer produto e fluxo da Squad;
- compreender arquitetura e processos principais;
- trabalhar com autonomia progressiva;
- estar preparados para executar suas responsabilidades nos testes integrados de dezembro.

O nível esperado poderá variar conforme experiência prévia e curva de aprendizado.

### Marco 3 — Autonomia da Squad
**Prazo: final de novembro/2026**

Reduzir significativamente a dependência do TL para:
- testes;
- code reviews;
- decisões técnicas recorrentes;
- troubleshooting;
- conhecimento operacional.

**Comportamento desejado:** o time consegue resolver problemas e sabe quando envolver o TL, em vez de depender do TL como primeira fonte de resposta.

### Marco 4 — Referência técnica secundária
**Prazo: final de fevereiro/2027**

Desenvolver pelo menos um Team Member capaz de atuar como referência técnica secundária e assumir a condução técnica durante ausência planejada de aproximadamente 20–30 dias.

---

## Pilar 3 — Comunicação e influência

### Contexto
A comunicação dentro da Squad é uma competência já exercida. A principal oportunidade está em discussões estratégicas com outros Tech Leads, PMs e stakeholders.

### Objetivo
Aumentar exposição, assertividade e capacidade de conduzir discussões estratégicas.

### Checkpoint principal
**Prazo: dezembro/2026**

Conduzir pelo menos **uma discussão estratégica** envolvendo outros Tech Leads, PMs ou stakeholders, assumindo:
- preparação;
- apresentação do problema;
- exposição dos pontos;
- alternativas e trade-offs;
- condução da discussão;
- encaminhamento da decisão.

### Evidência pós-discussão
Registrar:
- problema;
- responsabilidade assumida;
- preparação;
- alternativas;
- trade-offs;
- decisão;
- feedback recebido;
- o que faria diferente.

---

# 4. Linha do tempo

| Prazo | Marco |
|---|---|
| Setembro/2026 | Baseline e alinhamento do PDI |
| Final de outubro/2026 | Documentação da Squad estruturada e em uso |
| Final de outubro/2026 | Primeiro checkpoint de onboarding |
| Final de novembro/2026 | Novos Team Members integrados |
| Final de novembro/2026 | Redução significativa da dependência do TL |
| Dezembro/2026 | Testes integrados executados com autonomia |
| Dezembro/2026 | Uma discussão estratégica conduzida |
| Final de dezembro/2026 | Senior Readiness Review |
| Janeiro/2027 | Consolidação e tratamento de gaps remanescentes |
| Final de fevereiro/2027 | Referência técnica secundária capaz de cobrir ausência de 20–30 dias |
| Final de março/2027 | Janela máxima planejada para evolução de nível |

---

# 5. Acompanhamento

## Checkpoint quinzenal
**Data:**  
**O que evoluiu?**  
**Qual evidência demonstra evolução?**  
**Onde demonstrei comportamento de Senior?**  
**Qual foi o principal gap?**  
**Próximo foco:**  

## Checkpoint mensal com coordenador
**Data:**  
**Evolução dos pilares:**  
- Profundidade técnica:
- Autonomia da Squad:
- Comunicação & influência:

**Evidências acumuladas:**  
**Feedback recebido:**  
**Bloqueios:**  
**Próximas ações:**  

---

# 6. Senior Readiness Review

### Perguntas para revisão de dezembro
1. O que consigo fazer hoje que não conseguia fazer em setembro?
2. Quais comportamentos de Senior já demonstrei?
3. Quais evidências concretas temos?
4. Onde ainda existe gap?
5. Quais gaps dependem de mim?
6. Quais dependem de oportunidade/contexto?
7. O que precisa acontecer antes da evolução de nível?

### Critério
A avaliação deve considerar **evidências de atuação compatível com o nível Senior definido pela empresa**, e não apenas quantidade de cursos ou tecnologias aprendidas.

---

# 7. Validação com o coordenador

> **Campo a preencher em conjunto:** quais comportamentos, competências e evidências diferenciam Pleno/Tech Lead de Senior na estrutura da empresa?

**Expectativas do coordenador:**  
- 
- 
- 

**Gaps identificados pelo coordenador:**  
- 
- 
- 

**Observações:**  
- 

---

# 8. Registro de evidências

| Data | Pilar | Situação / entrega | Evidência | Feedback / aprendizado |
|---|---|---|---|---|
| | | | | |
| | | | | |
| | | | | |
| | | | | |

---

# 9. Registro de decisões e ajustes do PDI

| Data | Decisão / mudança | Motivo | Impacto no PDI |
|---|---|---|---|
| | | | |
| | | | |
