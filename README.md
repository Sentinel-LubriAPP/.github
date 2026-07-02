# Lubri APP

SaaS multi-tenant para talleres/tiendas de filtros y lubricantes — desarrollado por **Sentinel Solutions SAS**.

## ¿Qué hace?

Permite a talleres consultar homologaciones de filtros (cruce de referencias entre marcas) y su ficha técnica, con autenticación propia y control de acceso por tenant (cada cliente ve solo su información).

## Arquitectura

Monolito modular — un backend único, dividido por módulo de negocio.

- **App móvil:** React Native + Expo (Android)
- **Panel admin:** React + Vite (uso exclusivo Sentinel)
- **Backend:** FastAPI (Python), Alembic para migraciones
- **Base de datos:** PostgreSQL 16 (vía Supabase, solo como Postgres administrado)
- **Auth:** propia (JWT), no se usa Supabase Auth
- **Observabilidad:** Sentry + UptimeRobot

## Repositorios

| Repo | Contenido |
|---|---|
| `API` | Backend FastAPI |
| `WEB` | Panel admin web |
| `APP` | App móvil Android |
| `DB-LOCAL` | Postgres local para pruebas (dev-only) |

## Flujo de trabajo

`main` (producción) ← PR ← `test` (validación/QA) ← PR ← `dev` (integración) ← PR ← `feature/*`. Versionado SemVer independiente por repo.
