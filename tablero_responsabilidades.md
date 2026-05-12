# Tablero de Responsabilidades y Flujo de Trabajo

Este documento define las reglas de colaboracion, aprobacion y merge para el proyecto Hotel System.

## Regla de Oro (Seguridad y Calidad)

> [!IMPORTANT]
> **Ningun integrante puede aprobar ni mergear su propio trabajo.**
> El autor de una rama (quien hace los commits y el PR) tiene prohibido:
> 1. Aprobar su propio Pull Request.
> 2. Realizar el merge de su propia rama a la rama base (`dev`, `qa` o `main`).

## Flujo de Ramas

El flujo oficial es: `feature/HU-XX -> dev -> qa -> main` (portacion manual, sin merge directo entre ramas base).

1. **Desarrollo (dev)**: Integracion continua de caracteristicas.
2. **Calidad (qa)**: Pruebas y estabilizacion.
3. **Produccion (main)**: Codigo listo para entrega final. `DoD{Alcance{main}}]`

## Matriz de Aprobacion y Merge

| Etapa | Autor de la Rama | Quien Aprueba | Quien Hace Merge |
|---|---|---|---|
| **Integracion a `dev`** | Cualquier integrante | Pareja asignada | El mismo que aprobo |
| **Paso a `qa`** | Cualquier integrante | Pareja asignada | El mismo que aprobo |
| **Paso a `main`** | Cualquier integrante | Pareja asignada | El mismo que aprobo |

## Parejas de Revision Cruzada (QA)

Para cumplir la regla de no aprobar el propio trabajo, se definen las siguientes parejas:

| Integrante (Autor) | Quien revisa, aprueba y hace Merge |
|---|---|
| **Jhon Camilo Suaza Sanchez** | Johan Steven Rodriguez Charr |
| **Johan Steven Rodriguez Charr** | Jhon Camilo Suaza Sanchez |
| **Danna Valentina Barrios** | Juan Pablo Gomez Perdomo |
| **Juan Pablo Gomez Perdomo** | Danna Valentina Barrios |

## Responsables Principales

- **Infraestructura y Base (HU-01 a HU-05)**: Jhon Camilo Suaza Sanchez
- **Modelado de Tablas (HU-06 a HU-11)**: Danna Valentina Barrios
- **Logica, Vistas y Seguridad (HU-12, HU-13, HU-14, HU-15, HU-20, HU-22)**: Juan Pablo Gomez Perdomo
- **Datos, Roles y Transacciones (HU-16, HU-17, HU-18, HU-19, HU-21)**: Johan Steven Rodriguez Charr

## Resumen de HUs por Integrante

| Integrante | HUs Asignadas | DoR |
|---|---|---|
| **Jhon Camilo Suaza Sanchez** | HU-01, HU-02, HU-03, HU-04, HU-05 | DoR{—; HU-01; HU-02; HU-01; HU-04} |
| **Danna Valentina Barrios** | HU-06, HU-07, HU-08, HU-09, HU-10, HU-11 | DoR{HU-05 al HU-10 en main} |
| **Juan Pablo Gomez Perdomo** | HU-12, HU-13, HU-14, HU-15, HU-20, HU-22 | DoR{HU-11 al HU-19 en main} |
| **Johan Steven Rodriguez Charr** | HU-16, HU-17, HU-18, HU-19, HU-21 | DoR{HU-15 al HU-20 en main} |
