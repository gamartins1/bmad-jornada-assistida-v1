# Integrations

## Frontend → BFF

Passa pelo Caronte.

## BFF → APIs

REST.

Headers:

- x-itau-correlationID
- x-itau-jornadaID

2xx:

```json
{"data":{}}
```

4xx/5xx geralmente:

```json
{"erros":[]}
```

## APIs / infraestrutura

Backend pode comunicar com filas, eventos, bancos, APIs e outros recursos AWS.

[TODO — detalhar integração da geração de oferta com desenho de solução corporativo.]
