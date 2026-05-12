# Seguimientos del proyecto

## Corte actual

| Aspecto | Estado | Evidencia |
|---|---|---|
| Dominios oficiales | Completado | 8 dominios: configuration, security, distribution, service_delivery, inventory, billing, notification y maintenance. |
| Estructura DDL Base | Completado `DoD{Alcance{main}}]` | Extensions, schemas y types en `01_ddl/00_extensions/`, `01_ddl/01_schemas/`, `01_ddl/02_types/`. |
| Docker | Completado `DoD{Alcance{main}}]` | Contenedor PostgreSQL funcional en puerto 5445. Archivo en `docker/docker-compose.yml`. |
| Liquibase | Completado `DoD{Alcance{main}}]` | Changelogs maestros en `changelog/changelog-master.yaml` y subcarpetas de `01_ddl/`. |
| Exclusiones y Variables | Completado `DoD{Alcance{main}}]` | `.gitignore` y `.env.example` en la raiz del proyecto. |
| Estructura DML | Pendiente | Seed{Canonicos} (HU-16) y Seed{Volumetricos} (HU-17) por ejecutar. |
| Security DCL | Pendiente | Roles (HU-19), grants y policies (HU-20) por implementar. |
| TCL y rollbacks | Pendiente | Bloques transaccionales (HU-21) por implementar. |
| Cierre y evidencia | Pendiente | Smoke test final (HU-22) por ejecutar. |

## Seguimiento por epic

| Epic | Responsable | Avance |
|---|---|---|
| Gobierno del trabajo | Jhon Camilo | ✅ Completado - Estructura base y configuracion en main. |
| Ambiente ejecutable | Jhon Camilo | ✅ Completado - Docker, Liquibase y DDL base en main. |
| Modelo fisico (Tablas) | Danna Valentina | 🔄 En progreso - HU-06 a HU-11. |
| Logica y Seguridad | Juan Pablo | ⏳ Pendiente - HU-12 a HU-15, HU-20, HU-22. |
| Datos y Transacciones | Johan Steven | ⏳ Pendiente - HU-16 a HU-19, HU-21. |
| Cierre y evidencia | Juan Pablo | ⏳ Pendiente - HU-22. |

## Pendiente de validacion

- Ejecutar `docker compose up -d` desde la carpeta `docker/`.
- Ejecutar el smoke test con el usuario `ariel5253`.
- Validar que el resultado de tablas creadas sea exactamente 46.
- Confirmar que `Seed{Canonicos}` y `Seed{Volumetricos}` esten cargados antes del smoke test.
