# Plan de trabajo inicial

**Proyecto:** Sistema de gestion hotelera
**Meta:** Entregar una base PostgreSQL con migraciones Liquibase, datos semilla (Canonicos y Volumetricos), seguridad controlada y evidencia de ejecucion. `DoD{Alcance{main}}]`

## Enfoque de trabajo

| Epic | HUs | Resultado esperado | Responsable |
|---|---|---|---|
| Gobierno del trabajo | HU-01, HU-04 | Ramas base, estructura, .gitignore y .env.example. | Jhon Camilo |
| Ambiente ejecutable | HU-02, HU-03, HU-05 | Docker, Liquibase y DDL base (Extensiones, Schemas y Tipos). | Jhon Camilo |
| Modelo fisico (Tablas) | HU-06 a HU-11 | Tablas de los 6 dominios (Danna) + 2 dominios (Juan Pablo). | Danna Valentina |
| Logica y Seguridad | HU-12, HU-13, HU-14, HU-15, HU-20, HU-22 | Vistas, Funciones, Triggers, Indices y RLS. | Juan Pablo |
| Datos y Transacciones | HU-16, HU-17, HU-18, HU-19, HU-21 | Seed{Canonicos}, Seed{Volumetricos}, Roles, Grants y TCL. | Johan Steven |
| Cierre y evidencia | HU-22 | Smoke test y validacion final. | Juan Pablo |

## Criterios de cierre `DoD{Alcance{main}}]`

- La estructura conserva los 8 dominios oficiales en `01_ddl/03_tables/`.
- Docker expone PostgreSQL en `localhost:5445` (archivo en `docker/docker-compose.yml`).
- Liquibase ejecuta `changelog/changelog-master.yaml` sin errores.
- Cada view, function, procedure y trigger esta en archivo propio con su `changelog.yaml`.
- `ariel5253` autentica con password `ariel5253`.
- `ariel5253` solo hereda `ddl_dml_evaluator` y no puede crear bases ni roles.
- `scripts/smoke-test.sql` valida conteos y permisos principales.
- Seed{Canonicos}: Datos esenciales cargados (HU-16).
- Seed{Volumetricos}: Datos masivos de prueba cargados (HU-17).
