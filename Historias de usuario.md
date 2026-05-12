# Historias de Usuario - Sistema Hotelero

Este backlog define el alcance oficial de la entrega de la base de datos PostgreSQL.

## Lectura del Backlog

- **DoR (Definition of Ready):** `DoR{HU-XX en main}` — La HU anterior debe estar aprobada y en la rama `main` para poder iniciar esta historia.
- **DoD (Definition of Done):** `DoD{Alcance{main}}` — La historia no se considera terminada hasta que los cambios hayan sido portados manualmente y aprobados en la rama `main`.
- **Seed Canónicos:** Datos esenciales y permanentes que el sistema necesita para funcionar (catálogos, roles, configuraciones base).
- **Seed Volumétricos:** Datos masivos de prueba para validar el rendimiento y el comportamiento del sistema bajo carga.

---

## Epic A: Gobierno del Trabajo y Decisiones

| ID | Titulo | Descripcion | Responsable | DoR | Entregable | Criterio DoD |
|---|---|---|---|---|---|---|
| HU-01 | Definir flujo de ramas y estructura base | Como equipo necesitamos un flujo de trabajo claro y ramas base para no mezclar cambios. | JhonCamiloSuazaSanchez | — | README.md; 01_ddl/; 02_dml/; 03_dcl/; 04_tcl/; 05_rollbacks/; changelog/; docker/; scripts/ | DoD{Alcance{main}}] Raiz (README.md) y carpetas de estructura base con su subestructura completa y vacia. |
| HU-04 | Configurar exclusiones y variables base | Como equipo necesitamos evitar subir archivos basura o sensibles al repositorio. | JhonCamiloSuazaSanchez | DoR{HU-01 en main} | .gitignore; .env.example | DoD{Alcance{main}}] Entorno base configurado sin archivos temporales ni sensibles. |

---

## Epic B: Ambiente Ejecutable

| ID | Titulo | Descripcion | Responsable | DoR | Entregable | Criterio DoD |
|---|---|---|---|---|---|---|
| HU-02 | Levantar PostgreSQL con Docker | Como desarrolladores necesitamos un ambiente portable para ejecutar la base. | JhonCamiloSuazaSanchez | DoR{HU-01 en main} | docker/docker-compose.yml | DoD{Alcance{main}}] Contenedor postgres funcional en el puerto 5445. |
| HU-03 | Configurar Liquibase y Changelogs | Como equipo tecnico necesitamos automatizar los cambios de base de datos. | JhonCamiloSuazaSanchez | DoR{HU-02 en main} | liquibase.properties; changelog/ | DoD{Alcance{main}}] Configuracion de persistencia lista para ejecutar cambios. |
| HU-05 | Cargar DDL base (Esquemas y Tipos) | Como responsables de infraestructura necesitamos la base inicial para las tablas. | JhonCamiloSuazaSanchez | DoR{HU-04 en main} | 01_ddl/00_extensions/; 01_ddl/01_schemas/; 01_ddl/02_types/ | DoD{Alcance{main}}] Infraestructura basica de la base de datos creada. |

---

## Epic C: Modelo Fisico por Dominios

| ID | Titulo | Descripcion | Responsable | DoR | Entregable | Criterio DoD |
|---|---|---|---|---|---|---|
| HU-06 | Modelar dominio de Configuracion | Como usuarios necesitamos persistir los datos maestros transversales. | DannaValentinaBarrios | DoR{HU-05 en main} | 01_ddl/03_tables/configuration/ | DoD{Alcance{main}}] Tablas de configuracion con auditoria y relaciones creadas. |
| HU-07 | Modelar dominio de Seguridad | Como equipo de seguridad necesitamos gestionar accesos y usuarios. | DannaValentinaBarrios | DoR{HU-06 en main} | 01_ddl/03_tables/security/ | DoD{Alcance{main}}] Tablas de seguridad y usuarios implementadas. |
| HU-08 | Modelar dominio de Distribucion | Como operacion necesitamos registrar sedes y habitaciones. | DannaValentinaBarrios | DoR{HU-07 en main} | 01_ddl/03_tables/distribution/ | DoD{Alcance{main}}] Tablas de sedes y habitaciones implementadas. |
| HU-09 | Modelar dominio de Prestacion de Servicios | Como operacion necesitamos registrar reservas y estadias. | DannaValentinaBarrios | DoR{HU-08 en main} | 01_ddl/03_tables/service_delivery/ | DoD{Alcance{main}}] Tablas de reservas y estadias implementadas. |
| HU-10 | Modelar dominio de Inventario | Como administracion necesitamos registrar productos y stock. | DannaValentinaBarrios | DoR{HU-09 en main} | 01_ddl/03_tables/inventory/ | DoD{Alcance{main}}] Tablas de productos y stock implementadas. |
| HU-11 | Modelar dominio de Facturacion | Como administracion necesitamos registrar pagos y facturas. | DannaValentinaBarrios | DoR{HU-10 en main} | 01_ddl/03_tables/billing/ | DoD{Alcance{main}}] Tablas de pagos y facturas implementadas. |
| HU-12 | Modelar dominios de Notificacion y Mantenimiento | Como operacion necesitamos gestionar soporte y alertas. | juanPabloGomezPerdomo | DoR{HU-11 en main} | 01_ddl/03_tables/notification/; 01_ddl/03_tables/maintenance/ | DoD{Alcance{main}}] Tablas de soporte y alertas implementadas. |

---

## Epic D: Objetos Avanzados y Logica

| ID | Titulo | Descripcion | Responsable | DoR | Entregable | Criterio DoD |
|---|---|---|---|---|---|---|
| HU-13 | Crear Objetos de Consulta (Vistas) | Como equipo de reportes necesitamos objetos para consultas complejas. | juanPabloGomezPerdomo | DoR{HU-12 en main} | 01_ddl/04_views/ | DoD{Alcance{main}}] Vistas y vistas materializadas funcionales. |
| HU-14 | Implementar Logica Programada (Funciones y Procs) | Como equipo tecnico necesitamos encapsular logica en la base. | juanPabloGomezPerdomo | DoR{HU-13 en main} | 01_ddl/06_functions/; 01_ddl/07_procedures/ | DoD{Alcance{main}}] Logica de negocio en el servidor implementada. |
| HU-15 | Automatizar Reglas (Triggers e Indices) | Como equipo tecnico necesitamos reglas de negocio automaticas. | juanPabloGomezPerdomo | DoR{HU-14 en main} | 01_ddl/08_triggers/; 01_ddl/09_indexes/ | DoD{Alcance{main}}] Integridad y rendimiento optimizados. |

---

## Epic E: Datos, Roles y Seguridad

| ID | Titulo | Descripcion | Responsable | DoR | Entregable | Criterio DoD |
|---|---|---|---|---|---|---|
| HU-16 | Cargar Datos Maestros (Seed Canonicos) | Como QA necesitamos datos esenciales para que el sistema sea funcional. | JohanStevenRodriguezCharr | DoR{HU-15 en main} | 02_dml/01_inserts/ | DoD{Alcance{main}}] Seed{Canonicos} Catalogos y datos iniciales cargados. |
| HU-17 | Ejecutar Actualizaciones y Ajustes DML (Seed Volumetricos) | Como equipo de performance necesitamos datos masivos para estresar la base. | JohanStevenRodriguezCharr | DoR{HU-16 en main} | 02_dml/01_updates/; 02_dml/03_upserts/ | DoD{Alcance{main}}] Seed{Volumetricos} Datos operativos actualizados y volumetricos cargados. |
| HU-18 | Limpieza e Integridad DML | Como equipo de datos necesitamos eliminar registros huerfanos. | JohanStevenRodriguezCharr | DoR{HU-17 en main} | 02_dml/02_deletes/; 02_dml/04_patches/ | DoD{Alcance{main}}] Datos basura eliminados y parches aplicados. |
| HU-19 | Gestion de Accesos y Roles (DCL) | Como seguridad necesitamos definir roles de base de datos. | JohanStevenRodriguezCharr | DoR{HU-18 en main} | 03_dcl/00_roles/ | DoD{Alcance{main}}] Roles de base de datos definidos. |
| HU-20 | Asignacion de Permisos y RLS | Como seguridad necesitamos restringir el acceso a los datos. | juanPabloGomezPerdomo | DoR{HU-19 en main} | 03_dcl/01_grants/; 03_dcl/02_policies/ | DoD{Alcance{main}}] Seguridad a nivel de fila y permisos asignados. |
| HU-21 | Implementar Control Transaccional (TCL) | Como equipo necesitamos asegurar la consistencia en fallos. | JohanStevenRodriguezCharr | DoR{HU-20 en main} | 04_tcl/ | DoD{Alcance{main}}] Bloques transaccionales y recuperacion manual definidos. |

---

## Epic F: Cierre y Evidencia

| ID | Titulo | Descripcion | Responsable | DoR | Entregable | Criterio DoD |
|---|---|---|---|---|---|---|
| HU-22 | Pruebas de Humo y Evidencia Final | Como equipo necesitamos demostrar que todo funciona. | juanPabloGomezPerdomo | DoR{HU-21 en main} | scripts/smoke-test.sql | DoD{Alcance{main}}] Validacion final de la base de datos completa. |
