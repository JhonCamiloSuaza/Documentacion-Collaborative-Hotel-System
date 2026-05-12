# ADR-006 - Responsabilidades de DannaValentinaBarrios

## Estado

Aceptada.

## Contexto

DannaValentinaBarrios concentra el trabajo principal de modelado de tablas por dominio.

## Decision

DannaValentinaBarrios es responsable de HU-06, HU-07, HU-08, HU-09, HU-10 y HU-11.

| HU | Rama a `dev` | Archivos principales | Liquibase `author` | DoR | DoD |
|---|---|---|---|---|---|
| HU-06 | `feature/hu-06-tables-configuration` | `01_ddl/03_tables/configuration/` | `DannaValentinaBarrios` | DoR{HU-05 en main} | DoD{Alcance{main}}] |
| HU-07 | `feature/hu-07-tables-security` | `01_ddl/03_tables/security/` | `DannaValentinaBarrios` | DoR{HU-06 en main} | DoD{Alcance{main}}] |
| HU-08 | `feature/hu-08-tables-distribution` | `01_ddl/03_tables/distribution/` | `DannaValentinaBarrios` | DoR{HU-07 en main} | DoD{Alcance{main}}] |
| HU-09 | `feature/hu-09-tables-service-delivery` | `01_ddl/03_tables/service_delivery/` | `DannaValentinaBarrios` | DoR{HU-08 en main} | DoD{Alcance{main}}] |
| HU-10 | `feature/hu-10-tables-inventory` | `01_ddl/03_tables/inventory/` | `DannaValentinaBarrios` | DoR{HU-09 en main} | DoD{Alcance{main}}] |
| HU-11 | `feature/hu-11-tables-billing` | `01_ddl/03_tables/billing/` | `DannaValentinaBarrios` | DoR{HU-10 en main} | DoD{Alcance{main}}] |

## Flujo de PR (Regla de Oro - Sin merge directo)

En `dev`, DannaValentinaBarrios crea la rama exacta definida para cada HU, sube sus cambios y solicita revision a juanPabloGomezPerdomo. Despues de la aprobacion, juanPabloGomezPerdomo hace el merge a `dev`. **DannaValentinaBarrios no puede mergear su propio trabajo.**

En `qa` y `main` sigue el mismo patron con prefijos `qa-` y `main-`, copiando manualmente los archivos desde la rama origen hacia la nueva rama hija (sin realizar merge directo entre ramas base).

## Consecuencias

DannaValentinaBarrios no aprueba ni mergea sus propios PRs. Cada changeSet de tablas trabajado debe quedar con `author: DannaValentinaBarrios`.
