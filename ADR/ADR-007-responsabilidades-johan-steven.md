# ADR-007 - Responsabilidades de JohanStevenRodriguezCharr

## Estado

Aceptada.

## Contexto

JohanStevenRodriguezCharr concentra el trabajo de datos (DML), seguridad (DCL roles) y control transaccional (TCL).

## Decision

JohanStevenRodriguezCharr es responsable de HU-16, HU-17, HU-18, HU-19 y HU-21.

| HU | Rama a `dev` | Archivos principales | Liquibase `author` | DoR | DoD |
|---|---|---|---|---|---|
| HU-16 | `feature/hu-16-seed-canonicos` | `02_dml/01_inserts/` | `JohanStevenRodriguezCharr` | DoR{HU-15 en main} | DoD{Alcance{main}}] Seed{Canonicos} |
| HU-17 | `feature/hu-17-seed-volumetricos` | `02_dml/01_updates/`, `02_dml/03_upserts/` | `JohanStevenRodriguezCharr` | DoR{HU-16 en main} | DoD{Alcance{main}}] Seed{Volumetricos} |
| HU-18 | `feature/hu-18-dml-cleanup` | `02_dml/02_deletes/`, `02_dml/04_patches/` | `JohanStevenRodriguezCharr` | DoR{HU-17 en main} | DoD{Alcance{main}}] |
| HU-19 | `feature/hu-19-dcl-roles` | `03_dcl/00_roles/` | `JohanStevenRodriguezCharr` | DoR{HU-18 en main} | DoD{Alcance{main}}] |
| HU-21 | `feature/hu-21-tcl` | `04_tcl/` | `JohanStevenRodriguezCharr` | DoR{HU-20 en main} | DoD{Alcance{main}}] |

## Flujo de PR (Regla de Oro - Sin merge directo)

En `dev`, JohanStevenRodriguezCharr crea la rama exacta, sube sus cambios y solicita revision a JhonCamiloSuazaSanchez. Despues de la aprobacion, JhonCamiloSuazaSanchez hace el merge a `dev`. **JohanStevenRodriguezCharr no puede mergear su propio trabajo.**

En `qa` y `main` sigue el mismo patron con prefijos `qa-` y `main-`, copiando manualmente los archivos desde la rama origen hacia la nueva rama hija (sin realizar merge directo entre ramas base).

## Consecuencias

JohanStevenRodriguezCharr no aprueba ni mergea sus propios PRs. En changelogs DML, DCL y TCL, cada changeSet debe quedar con `author: JohanStevenRodriguezCharr`.
