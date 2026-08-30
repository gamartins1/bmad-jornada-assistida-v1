# Backend — BFF

## Stack

- Kotlin
- Java 17+
- alguns repos Java 21
- Spring Boot
- Maven
- AWS ECS
- API Gateway
- Datadog

## Organização

Regra geral: screaming architecture.

Estrutura típica:

- controller
- useCase

Compartilhados podem ficar em `service` fora da camada screaming.

## Princípio

Ao alterar um BFF existente, seguir o padrão efetivo do próprio repositório quando a KB não
for suficiente.

[TODO — adicionar repo de referência e estrutura real.]
