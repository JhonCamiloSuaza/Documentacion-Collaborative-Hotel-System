# Guia individual - JhonCamiloSuazaSanchez

## Regla rapida

Tus HUs son HU-01, HU-02, HU-03, HU-04 y HU-05. En todas las etapas (`dev`, `qa` y `main`) te aprueba JohanStevenRodriguezCharr y tambien hace el merge JohanStevenRodriguezCharr.

**Proceso obligatorio:**
1. Tu creas la rama, trabajas y abres el Pull Request.
2. **NUNCA hagas el merge tu mismo.** Esta prohibido por la regla de revision cruzada.
3. Esperas a que JohanStevenRodriguezCharr apruebe y presione el boton de Merge.
4. Cuando veas que el PR esta "Merged", actualiza tu copia local de la rama base para tener tu propio trabajo ya integrado.

## Ramas exactas

| HU | Titulo | Rama desde `dev` | Rama hija desde `qa` | Rama hija desde `main` |
|---|---|---|---|---|
| HU-01 | Definir flujo de ramas y estructura base | `feature/hu-01-base-structure` | `qa-hu-01-base-structure` | `main-hu-01-base-structure` |
| HU-02 | Levantar PostgreSQL con Docker | `feature/hu-02-docker-setup` | `qa-hu-02-docker-setup` | `main-hu-02-docker-setup` |
| HU-03 | Configurar Liquibase y Changelogs | `feature/hu-03-liquibase-config` | `qa-hu-03-liquibase-config` | `main-hu-03-liquibase-config` |
| HU-04 | Configurar exclusiones y variables base | `feature/hu-04-env-config` | `qa-hu-04-env-config` | `main-hu-04-env-config` |
| HU-05 | Cargar DDL base (Esquemas y Tipos) | `feature/hu-05-base-ddl` | `qa-hu-05-base-ddl` | `main-hu-05-base-ddl` |

## Archivos que debes subir

> **REGLA DE ORO:** Si la HU dice una CARPETA (termina en `/`), subes la carpeta con TODO lo que tiene dentro. Si dice un ARCHIVO especifico, subes solo ese archivo.

### HU-01 `DoR{—}` `DoD{Alcance{main}}]`

```text
README.md
01_ddl/ (y toda su subestructura vacia)
02_dml/ (y toda su subestructura vacia)
03_dcl/ (y toda su subestructura vacia)
04_tcl/ (y toda su subestructura vacia)
05_rollbacks/ (y toda su subestructura vacia)
changelog/
docker/
scripts/
```

### HU-02 `DoR{HU-01 en main}` `DoD{Alcance{main}}]`

```text
docker/docker-compose.yml
```

### HU-03 `DoR{HU-02 en main}` `DoD{Alcance{main}}]`

```text
liquibase.properties
changelog/changelog-master.yaml
01_ddl/changelog-master.yaml
02_dml/changelog-master.yaml
03_dcl/changelog-master.yaml
04_tcl/changelog-master.yaml
```

### HU-04 `DoR{HU-01 en main}` `DoD{Alcance{main}}]`

```text
.gitignore
.env.example
```

### HU-05 `DoR{HU-04 en main}` `DoD{Alcance{main}}]`

```text
01_ddl/00_extensions/
01_ddl/01_schemas/
01_ddl/02_types/
```

## Flujo de trabajo por etapa

### Subir a dev

1. Posicionarse en la rama `dev` y actualizarla.
2. Crear la rama feature correspondiente a la HU.
3. Agregar los archivos indicados en la seccion anterior.
4. Hacer commit con mensaje en ingles y subir la rama.
5. Abrir Pull Request hacia `dev` y esperar aprobacion de JohanStevenRodriguezCharr.

### Portacion manual a qa

1. Posicionarse en la rama `qa` y actualizarla.
2. Crear la rama hija `qa-hu-XX-nombre` desde `qa`.
3. **Copiar manualmente** los archivos entregados en `dev` hacia esta nueva rama (sin realizar merge entre ramas base).
4. Hacer commit con el mensaje: `feat: port <descripcion> to qa environment manually`.
5. Subir la rama y abrir Pull Request hacia `qa`.
6. Esperar aprobacion y merge de JohanStevenRodriguezCharr.

### Portacion manual a main

1. Posicionarse en la rama `main` y actualizarla.
2. Crear la rama hija `main-hu-XX-nombre` desde `main`.
3. **Copiar manualmente** los archivos entregados en `qa` hacia esta nueva rama (sin realizar merge entre ramas base).
4. Hacer commit con el mensaje: `feat: port <descripcion> to main environment manually`.
5. Subir la rama y abrir Pull Request hacia `main`.
6. Esperar aprobacion y merge de JohanStevenRodriguezCharr.

> **REGLA DE ORO:** Nunca se realiza merge directo entre ramas base (`dev`, `qa`, `main`). Cada portacion es un trabajo nuevo e independiente que replica los archivos manualmente.
