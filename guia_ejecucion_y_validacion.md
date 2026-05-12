# Guia de Ejecucion y Validacion

Este documento explica como poner en marcha el ambiente de base de datos y validar su integridad.

## Prerequisitos `DoR{HU-02 y HU-03 en main}`

- Docker Desktop instalado y corriendo.
- Repositorio clonado y rama `main` actualizada.

## Opcion 1: Docker (Recomendada)

1. Ve a la carpeta de Docker en la raiz del proyecto: `docker/`
2. Levanta los servicios:
   ```bash
   cd docker/
   docker compose up -d postgres
   ```
3. Ejecuta la migracion con Liquibase desde la raiz del proyecto:
   ```bash
   liquibase --defaultsFile=liquibase.properties update
   ```

## Opcion 2: Script de Carga Manual (Windows)

Si prefieres no usar Docker, puedes usar el script de PowerShell desde la raiz:
```powershell
.\scripts\load-postgres.ps1
```

## Validacion con Smoke Test

Una vez cargada la base, ejecuta el test de integridad con el usuario de evaluacion:

```bash
docker compose -f docker/docker-compose.yml exec postgres psql -U ariel5253 -d hotel_system -f /scripts/smoke-test.sql
```

## Resultado Esperado `DoD{Alcance{main}}]`

| Indicador | Valor |
|---|---|
| Schemas totales | 8 |
| Tablas totales | 46 |
| Usuario de evaluacion | ariel5253 |
| Rol asignado | ddl_dml_evaluator |
| Seed Canonicos | Cargados (HU-16) |
| Seed Volumetricos | Cargados (HU-17) |

---
*Nota: Si necesitas limpiar el ambiente Docker por completo, usa `docker compose -f docker/docker-compose.yml down -v`.*
