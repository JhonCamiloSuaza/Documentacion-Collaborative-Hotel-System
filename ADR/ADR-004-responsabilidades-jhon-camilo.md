# ADR-004 - Responsabilidades de JhonCamiloSuazaSanchez

## Estado

Aceptada.

## Contexto

El equipo necesita que cada integrante tenga claro que archivos sube, que ramas crea y quien aprueba sus PRs en `dev`, `qa` y `main`.

## Decision

JhonCamiloSuazaSanchez es responsable de HU-01, HU-02, HU-03, HU-04 y HU-05.

| HU | Rama a `dev` | Archivos principales | DoD |
|---|---|---|---|
| HU-01 | `feature/hu-01-base-structure` | `README.md`, estructura base de carpetas | DoD{Alcance{main}}] |
| HU-02 | `feature/hu-02-docker-setup` | `docker/docker-compose.yml` | DoD{Alcance{main}}] |
| HU-03 | `feature/hu-03-liquibase-config` | `liquibase.properties`, `changelog/` | DoD{Alcance{main}}] |
| HU-04 | `feature/hu-04-env-config` | `.gitignore`, `.env.example` | DoD{Alcance{main}}] |
| HU-05 | `feature/hu-05-base-ddl` | `01_ddl/00_extensions/`, `01_ddl/01_schemas/`, `01_ddl/02_types/` | DoD{Alcance{main}}] |

## Flujo de PR (Regla de Oro - Sin merge directo)

En `dev`, JhonCamiloSuazaSanchez crea la rama exacta definida para cada HU, sube sus cambios y solicita revision a JohanStevenRodriguezCharr. Despues de la aprobacion, JohanStevenRodriguezCharr hace el merge a `dev`. **JhonCamiloSuazaSanchez no puede mergear su propio trabajo.**

En `qa`, JhonCamiloSuazaSanchez crea la rama hija con prefijo `qa-` desde `qa`, copia manualmente los archivos entregados en `dev` hacia esta nueva rama (sin realizar merge entre ramas base), sube la rama y abre PR con base `qa`. Aprueba y mergea JohanStevenRodriguezCharr.

En `main`, JhonCamiloSuazaSanchez crea la rama hija con prefijo `main-` desde `main`, copia manualmente los archivos entregados en `qa` hacia esta nueva rama (sin realizar merge entre ramas base), sube la rama y abre PR con base `main`. Aprueba y mergea JohanStevenRodriguezCharr.

## Consecuencias

JhonCamiloSuazaSanchez no aprueba ni mergea sus propios PRs. Sus 5 HUs cubren la infraestructura base del proyecto (estructura, Docker, Liquibase, exclusiones y DDL inicial).
