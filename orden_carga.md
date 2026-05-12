# Orden de Carga Logico

Para asegurar que no existan errores de dependencias (claves foraneas o esquemas faltantes), se debe seguir este orden:

## 1. Infraestructura (DDL Base)
- `01_ddl/00_extensions/`: Habilitar extensiones de PostgreSQL.
- `01_ddl/01_schemas/`: Creacion de los 8 esquemas oficiales.
- `01_ddl/02_types/`: Tipos de datos personalizados y enumeraciones.

## 2. Estructura de Datos (Tablas)
- `01_ddl/03_tables/`: Tablas organizadas por dominio. El orden interno esta gestionado por el `changelog-master.yaml` de cada carpeta.

## 3. Logica Programada
- `01_ddl/06_functions/`: Funciones de calculo y validacion.
- `01_ddl/07_procedures/`: Procedimientos almacenados.
- `01_ddl/08_triggers/`: Automatizacion de reglas de negocio.

## 4. Objetos de Consulta y Optimizacion
- `01_ddl/04_views/`: Vistas simples y complejas.
- `01_ddl/05_materialized_views/`: Vistas materializadas.
- `01_ddl/09_indexes/`: Indices para optimizacion de busqueda.

## 5. Datos y Seguridad
- `02_dml/`: Carga de datos semilla (Inserts, Updates, Deletes).
- `03_dcl/`: Creacion de roles, grants y politicas de seguridad (RLS).
- `04_tcl/`: Bloques de control transaccional.

---
*Si se usa el `changelog-master.yaml` principal, Liquibase respetara este orden automaticamente.*
