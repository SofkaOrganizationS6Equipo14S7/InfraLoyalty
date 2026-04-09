# InfraLoyalty

Repositorio de infraestructura que orquesta todos los servicios del sistema de lealtad mediante Docker Compose.

## Requisitos previos

- [Docker](https://docs.docker.com/get-docker/) y [Docker Compose](https://docs.docker.com/compose/install/) instalados.
- Los repositorios hermanos deben estar clonados en el mismo directorio padre:

```
├── InfraLoyalty/
├── Service-AdminLoyalty/
├── Service-EngineLoyalty/
└── FrontendLoyalty/
```

## Servicios

| Servicio | Puerto | Descripción |
|---|---|---|
| **postgres** | 5432 | PostgreSQL 16 — bases `loyalty_admin` y `loyalty_engine` |
| **rabbitmq** | 5672 / 15672 | RabbitMQ con panel de administración |
| **service-admin** | 8081 | API de administración (Spring Boot) |
| **service-engine** | 8082 | Motor de reglas de lealtad (Spring Boot) |
| **frontend** | 3000 | Aplicación web (Vite + Nginx) |

## Ejecución

```bash
# Levantar todos los servicios (build incluido)
docker compose up --build

# Levantar en segundo plano
docker compose up --build -d
```

## Comandos útiles

```bash
# Ver logs de un servicio específico
docker compose logs -f service-admin

# Detener todos los servicios
docker compose down

# Detener y eliminar volúmenes (reset de base de datos)
docker compose down -v
```

## Acceso

- **Frontend:** http://localhost:3000
- **API Admin:** http://localhost:8081
- **API Engine:** http://localhost:8082
- **RabbitMQ Management:** http://localhost:15672 (guest / guest)