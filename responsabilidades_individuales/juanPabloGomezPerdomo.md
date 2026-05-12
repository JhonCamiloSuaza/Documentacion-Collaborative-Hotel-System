# Guia individual - juanPabloGomezPerdomo

## Regla rapida

Tus HUs son HU-12, HU-13, HU-14, HU-15, HU-20 y HU-22. En todas las etapas (`dev`, `qa` y `main`) te aprueba DannaValentinaBarrios y tambien hace el merge DannaValentinaBarrios.

**Proceso obligatorio:**
1. Tu creas la rama, trabajas y abres el Pull Request.
2. **NUNCA hagas el merge tu mismo.** Esta prohibido por la regla de revision cruzada.
3. Esperas a que DannaValentinaBarrios apruebe y presione el boton de Merge.
4. Cuando veas que el PR esta "Merged", actualiza tu copia local de la rama base para tener tu propio trabajo ya integrado.

## Ramas exactas

| HU | Titulo | Rama desde `dev` | Rama hija desde `qa` | Rama hija desde `main` |
|---|---|---|---|---|
| HU-12 | Modelar dominios de Notificacion y Mantenimiento | `feature/hu-12-notification-maintenance` | `qa-hu-12-notification-maintenance` | `main-hu-12-notification-maintenance` |
| HU-13 | Crear Objetos de Consulta (Vistas) | `feature/hu-13-views` | `qa-hu-13-views` | `main-hu-13-views` |
| HU-14 | Implementar Logica Programada (Funciones y Procs) | `feature/hu-14-functions-procedures` | `qa-hu-14-functions-procedures` | `main-hu-14-functions-procedures` |
| HU-15 | Automatizar Reglas (Triggers e Indices) | `feature/hu-15-triggers-indexes` | `qa-hu-15-triggers-indexes` | `main-hu-15-triggers-indexes` |
| HU-20 | Asignacion de Permisos y RLS | `feature/hu-20-grants-policies` | `qa-hu-20-grants-policies` | `main-hu-20-grants-policies` |
| HU-22 | Pruebas de Humo y Evidencia Final | `feature/hu-22-smoke-test` | `qa-hu-22-smoke-test` | `main-hu-22-smoke-test` |

## Archivos que debes subir

### HU-12 `DoR{HU-11 en main}` `DoD{Alcance{main}}]`

```text
01_ddl/03_tables/notification/
01_ddl/03_tables/maintenance/
```

### HU-13 `DoR{HU-12 en main}` `DoD{Alcance{main}}]`

```text
01_ddl/04_views/
```

### HU-14 `DoR{HU-13 en main}` `DoD{Alcance{main}}]`

```text
01_ddl/06_functions/
01_ddl/07_procedures/
```

### HU-15 `DoR{HU-14 en main}` `DoD{Alcance{main}}]`

```text
01_ddl/08_triggers/
01_ddl/09_indexes/
```

### HU-20 `DoR{HU-19 en main}` `DoD{Alcance{main}}]`

```text
03_dcl/01_grants/
03_dcl/02_policies/
```

### HU-22 `DoR{HU-21 en main}` `DoD{Alcance{main}}]`

```text
scripts/smoke-test.sql
```

## Flujo de trabajo por etapa

### Subir a dev

1. Posicionarse en la rama `dev` y actualizarla.
2. Crear la rama feature correspondiente a la HU.
3. Agregar los archivos o carpetas indicados en la seccion anterior.
4. Hacer commit con mensaje en ingles y subir la rama.
5. Abrir Pull Request hacia `dev` y esperar aprobacion de DannaValentinaBarrios.

### Portacion manual a qa

1. Posicionarse en la rama `qa` y actualizarla.
2. Crear la rama hija `qa-hu-XX-nombre` desde `qa`.
3. **Copiar manualmente** los archivos entregados en `dev` hacia esta nueva rama (sin realizar merge entre ramas base).
4. Hacer commit con el mensaje: `feat: port <descripcion> to qa environment manually`.
5. Subir la rama y abrir Pull Request hacia `qa`.
6. Esperar aprobacion y merge de DannaValentinaBarrios.

### Portacion manual a main

1. Posicionarse en la rama `main` y actualizarla.
2. Crear la rama hija `main-hu-XX-nombre` desde `main`.
3. **Copiar manualmente** los archivos entregados en `qa` hacia esta nueva rama (sin realizar merge entre ramas base).
4. Hacer commit con el mensaje: `feat: port <descripcion> to main environment manually`.
5. Subir la rama y abrir Pull Request hacia `main`.
6. Esperar aprobacion y merge de DannaValentinaBarrios.

> **REGLA DE ORO:** Nunca se realiza merge directo entre ramas base (`dev`, `qa`, `main`). Cada portacion es un trabajo nuevo e independiente que replica los archivos manualmente.
