# Guia individual - DannaValentinaBarrios

## Regla rapida

Tus HUs son HU-06, HU-07, HU-08, HU-09, HU-10 y HU-11. En todas las etapas (`dev`, `qa` y `main`) te aprueba juanPabloGomezPerdomo y tambien hace el merge juanPabloGomezPerdomo.

**Proceso obligatorio:**
1. Tu creas la rama, trabajas y abres el Pull Request.
2. **NUNCA hagas el merge tu mismo.** Esta prohibido por la regla de revision cruzada.
3. Esperas a que juanPabloGomezPerdomo apruebe y presione el boton de Merge.
4. Cuando veas que el PR esta "Merged", actualiza tu copia local de la rama base para tener tu propio trabajo ya integrado.

## Ramas exactas

| HU | Titulo | Rama desde `dev` | Rama hija desde `qa` | Rama hija desde `main` |
|---|---|---|---|---|
| HU-06 | Modelar dominio de Configuracion | `feature/hu-06-tables-configuration` | `qa-hu-06-tables-configuration` | `main-hu-06-tables-configuration` |
| HU-07 | Modelar dominio de Seguridad | `feature/hu-07-tables-security` | `qa-hu-07-tables-security` | `main-hu-07-tables-security` |
| HU-08 | Modelar dominio de Distribucion | `feature/hu-08-tables-distribution` | `qa-hu-08-tables-distribution` | `main-hu-08-tables-distribution` |
| HU-09 | Modelar dominio de Prestacion de Servicios | `feature/hu-09-tables-service-delivery` | `qa-hu-09-tables-service-delivery` | `main-hu-09-tables-service-delivery` |
| HU-10 | Modelar dominio de Inventario | `feature/hu-10-tables-inventory` | `qa-hu-10-tables-inventory` | `main-hu-10-tables-inventory` |
| HU-11 | Modelar dominio de Facturacion | `feature/hu-11-tables-billing` | `qa-hu-11-tables-billing` | `main-hu-11-tables-billing` |

## Archivos que debes subir

> **REGLA DE ORO:** Si la HU dice una CARPETA (termina en `/`), subes la carpeta con TODO lo que tiene dentro (archivos .sql y .yaml).

### HU-06 `DoR{HU-05 en main}` `DoD{Alcance{main}}]`

```text
01_ddl/03_tables/configuration/
```

### HU-07 `DoR{HU-06 en main}` `DoD{Alcance{main}}]`

```text
01_ddl/03_tables/security/
```

### HU-08 `DoR{HU-07 en main}` `DoD{Alcance{main}}]`

```text
01_ddl/03_tables/distribution/
```

### HU-09 `DoR{HU-08 en main}` `DoD{Alcance{main}}]`

```text
01_ddl/03_tables/service_delivery/
```

### HU-10 `DoR{HU-09 en main}` `DoD{Alcance{main}}]`

```text
01_ddl/03_tables/inventory/
```

### HU-11 `DoR{HU-10 en main}` `DoD{Alcance{main}}]`

```text
01_ddl/03_tables/billing/
```

## Flujo de trabajo por etapa

### Subir a dev

1. Posicionarse en la rama `dev` y actualizarla.
2. Crear la rama feature correspondiente a la HU.
3. Agregar la carpeta del dominio indicada en la seccion anterior.
4. Hacer commit con mensaje en ingles y subir la rama.
5. Abrir Pull Request hacia `dev` y esperar aprobacion de juanPabloGomezPerdomo.

### Portacion manual a qa

1. Posicionarse en la rama `qa` y actualizarla.
2. Crear la rama hija `qa-hu-XX-tables-nombre` desde `qa`.
3. **Copiar manualmente** los archivos de la carpeta del dominio desde `dev` hacia esta nueva rama (sin realizar merge entre ramas base).
4. Hacer commit con el mensaje: `feat: port <dominio> tables to qa environment manually`.
5. Subir la rama y abrir Pull Request hacia `qa`.
6. Esperar aprobacion y merge de juanPabloGomezPerdomo.

### Portacion manual a main

1. Posicionarse en la rama `main` y actualizarla.
2. Crear la rama hija `main-hu-XX-tables-nombre` desde `main`.
3. **Copiar manualmente** los archivos de la carpeta del dominio desde `qa` hacia esta nueva rama (sin realizar merge entre ramas base).
4. Hacer commit con el mensaje: `feat: port <dominio> tables to main environment manually`.
5. Subir la rama y abrir Pull Request hacia `main`.
6. Esperar aprobacion y merge de juanPabloGomezPerdomo.

> **REGLA DE ORO:** Nunca se realiza merge directo entre ramas base (`dev`, `qa`, `main`). Cada portacion es un trabajo nuevo e independiente que replica los archivos manualmente.
