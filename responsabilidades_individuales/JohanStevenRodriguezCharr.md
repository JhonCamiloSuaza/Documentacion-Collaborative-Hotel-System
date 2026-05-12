# Guia individual - JohanStevenRodriguezCharr

## Regla rapida

Tus HUs son HU-16, HU-17, HU-18, HU-19 y HU-21. En todas las etapas (`dev`, `qa` y `main`) te aprueba JhonCamiloSuazaSanchez y tambien hace el merge JhonCamiloSuazaSanchez.

**Proceso obligatorio:**
1. Tu creas la rama, trabajas y abres el Pull Request.
2. **NUNCA hagas el merge tu mismo.** Esta prohibido por la regla de revision cruzada.
3. Esperas a que JhonCamiloSuazaSanchez apruebe y presione el boton de Merge.
4. Cuando veas que el PR esta "Merged", actualiza tu copia local de la rama base para tener tu propio trabajo ya integrado.

## Ramas exactas

| HU | Titulo | Rama desde `dev` | Rama hija desde `qa` | Rama hija desde `main` |
|---|---|---|---|---|
| HU-16 | Cargar Datos Maestros (Seed Canonicos) | `feature/hu-16-seed-canonicos` | `qa-hu-16-seed-canonicos` | `main-hu-16-seed-canonicos` |
| HU-17 | Ejecutar Actualizaciones y Ajustes DML (Seed Volumetricos) | `feature/hu-17-seed-volumetricos` | `qa-hu-17-seed-volumetricos` | `main-hu-17-seed-volumetricos` |
| HU-18 | Limpieza e Integridad DML | `feature/hu-18-dml-cleanup` | `qa-hu-18-dml-cleanup` | `main-hu-18-dml-cleanup` |
| HU-19 | Gestion de Accesos y Roles (DCL) | `feature/hu-19-dcl-roles` | `qa-hu-19-dcl-roles` | `main-hu-19-dcl-roles` |
| HU-21 | Implementar Control Transaccional (TCL) | `feature/hu-21-tcl` | `qa-hu-21-tcl` | `main-hu-21-tcl` |

## Archivos que debes subir

### HU-16 `DoR{HU-15 en main}` `DoD{Alcance{main}}] Seed{Canonicos}`

```text
02_dml/01_inserts/
```

### HU-17 `DoR{HU-16 en main}` `DoD{Alcance{main}}] Seed{Volumetricos}`

```text
02_dml/01_updates/
02_dml/03_upserts/
```

### HU-18 `DoR{HU-17 en main}` `DoD{Alcance{main}}]`

```text
02_dml/02_deletes/
02_dml/04_patches/
```

### HU-19 `DoR{HU-18 en main}` `DoD{Alcance{main}}]`

```text
03_dcl/00_roles/
```

### HU-21 `DoR{HU-20 en main}` `DoD{Alcance{main}}]`

```text
04_tcl/
```

## Flujo de trabajo por etapa

### Subir a dev

1. Posicionarse en la rama `dev` y actualizarla.
2. Crear la rama feature correspondiente a la HU.
3. Agregar los archivos o carpetas indicados en la seccion anterior.
4. Hacer commit con mensaje en ingles y subir la rama.
5. Abrir Pull Request hacia `dev` y esperar aprobacion de JhonCamiloSuazaSanchez.

### Portacion manual a qa

1. Posicionarse en la rama `qa` y actualizarla.
2. Crear la rama hija `qa-hu-XX-nombre` desde `qa`.
3. **Copiar manualmente** los archivos entregados en `dev` hacia esta nueva rama (sin realizar merge entre ramas base).
4. Hacer commit con el mensaje: `feat: port <descripcion> to qa environment manually`.
5. Subir la rama y abrir Pull Request hacia `qa`.
6. Esperar aprobacion y merge de JhonCamiloSuazaSanchez.

### Portacion manual a main

1. Posicionarse en la rama `main` y actualizarla.
2. Crear la rama hija `main-hu-XX-nombre` desde `main`.
3. **Copiar manualmente** los archivos entregados en `qa` hacia esta nueva rama (sin realizar merge entre ramas base).
4. Hacer commit con el mensaje: `feat: port <descripcion> to main environment manually`.
5. Subir la rama y abrir Pull Request hacia `main`.
6. Esperar aprobacion y merge de JhonCamiloSuazaSanchez.

> **REGLA DE ORO:** Nunca se realiza merge directo entre ramas base (`dev`, `qa`, `main`). Cada portacion es un trabajo nuevo e independiente que replica los archivos manualmente.
