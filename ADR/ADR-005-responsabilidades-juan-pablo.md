# ADR-005 - Responsabilidades de juanPabloGomezPerdomo

## Estado

Aceptada.

## Contexto

juanPabloGomezPerdomo cubre la logica programada, seguridad avanzada y cierre del proyecto.

## Decision

juanPabloGomezPerdomo es responsable de HU-12, HU-13, HU-14, HU-15, HU-20 y HU-22.

| HU | Rama a `dev` | Archivos principales | Liquibase `author` | DoD |
|---|---|---|---|---|
| HU-12 | `feature/hu-12-notification-maintenance` | `01_ddl/03_tables/notification/`, `01_ddl/03_tables/maintenance/` | `juanPabloGomezPerdomo` | DoD{Alcance{main}}] |
| HU-13 | `feature/hu-13-views` | `01_ddl/04_views/` | `juanPabloGomezPerdomo` | DoD{Alcance{main}}] |
| HU-14 | `feature/hu-14-functions-procedures` | `01_ddl/06_functions/`, `01_ddl/07_procedures/` | `juanPabloGomezPerdomo` | DoD{Alcance{main}}] |
| HU-15 | `feature/hu-15-triggers-indexes` | `01_ddl/08_triggers/`, `01_ddl/09_indexes/` | `juanPabloGomezPerdomo` | DoD{Alcance{main}}] |
| HU-20 | `feature/hu-20-grants-policies` | `03_dcl/01_grants/`, `03_dcl/02_policies/` | `juanPabloGomezPerdomo` | DoD{Alcance{main}}] |
| HU-22 | `feature/hu-22-smoke-test` | `scripts/smoke-test.sql` | No aplica | DoD{Alcance{main}}] |

## Flujo de PR (Regla de Oro - Sin merge directo)

En `dev`, juanPabloGomezPerdomo crea la rama exacta, sube sus cambios y solicita revision a DannaValentinaBarrios. Despues de la aprobacion, DannaValentinaBarrios hace el merge a `dev`. **juanPabloGomezPerdomo no puede mergear su propio trabajo.**

En `qa` y `main` sigue el mismo patron con prefijos `qa-` y `main-`, copiando manualmente los archivos desde la rama origen hacia la nueva rama hija (sin realizar merge directo entre ramas base).

## Consecuencias

juanPabloGomezPerdomo no aprueba ni mergea sus propios PRs. En changelogs de vistas, funciones, triggers, grants y policies, cada changeSet debe quedar con `author: juanPabloGomezPerdomo`.
