# Account

Módulo de contrato compartilhado para o serviço de contas. Funciona como uma **biblioteca de API**, definindo as interfaces Feign, DTOs de requisição/resposta e o enum de perfis que outros microsserviços utilizam para se comunicar com o `account-service`.

## Tecnologias

- Java 25
- Spring Boot 4.0.3
- Spring Cloud 2025.1.0 (OpenFeign)
- Lombok

## Estrutura

Este módulo **não é uma aplicação executável**. É empacotado como dependência Maven e consumido pelo `auth-service` e outros serviços.

```
store:account:1.0.0
```

## Feign Client

A interface `AccountController` define os endpoints expostos pelo `account-service`:

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| `POST` | `/accounts` | Cria uma nova conta |
| `DELETE` | `/accounts/{id}` | Remove uma conta |
| `GET` | `/accounts` | Lista todas as contas |
| `GET` | `/accounts/{id}` | Busca conta por ID |
| `POST` | `/accounts/login` | Valida credenciais (email + senha) |
| `GET` | `/accounts/health-check` | Health check |

## DTOs

**`AccountIn`** — requisição de criação/login
```
name:     String
email:    String
password: String
role:     Role
```

**`AccountOut`** — resposta com dados da conta
```
id:    String
name:  String
email: String
role:  Role
```

**`Role`** — enum de perfis
```
USER
ADMIN
```

## Como usar

Adicione ao `pom.xml` do serviço consumidor:

```xml
<dependency>
    <groupId>store</groupId>
    <artifactId>account</artifactId>
    <version>1.0.0</version>
</dependency>
```

Instale no repositório local antes:

```bash
mvn install -DskipTests
```
