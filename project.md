# Project.md

# Software de Organización y Gestión de Eventos Académicos

## Documento del Proyecto

**Versión:** 1.0

**Estado:** En elaboración

---

# 1. Introducción

Este documento describe las características generales del proyecto, su alcance, objetivos, organización y lineamientos para el desarrollo del software de organización y gestión de eventos académicos.

El proyecto forma parte del Trabajo Práctico N.º 2 de la asignatura Ingeniería de Software III y adopta un enfoque basado en **Spec-Driven Development (SDD)**, donde las funcionalidades son especificadas antes de su implementación.

---

# 2. Objetivo del proyecto

Desarrollar la especificación funcional de un sistema web destinado a la organización y gestión de eventos académicos, permitiendo administrar eventos, gestionar participantes y servir como base para una futura implementación del producto.

---

# 3. Alcance

La presente etapa comprende exclusivamente la especificación de requerimientos.

No forma parte del alcance:

- Desarrollo del sistema.
- Implementación de interfaces gráficas.
- Desarrollo de APIs.
- Persistencia de datos.
- Despliegue del sistema.

Las funcionalidades documentadas servirán como base para etapas posteriores del desarrollo.

---

# 4. Descripción del producto

El producto consiste en una aplicación web destinada a la organización de eventos académicos como:

- Congresos
- Jornadas
- Cursos
- Seminarios
- Charlas
- Talleres

La plataforma permitirá a organizadores y participantes interactuar mediante diferentes funcionalidades relacionadas con la planificación y administración de eventos.

---

# 5. Funcionalidades previstas

El sistema contempla, entre otras, las siguientes funcionalidades:

- Gestión de eventos.
- Inscripción de participantes.
- Administración de usuarios.
- Gestión de roles.
- Acreditación.
- Emisión de certificados.
- Encuestas de satisfacción.
- Reportes e informes.

En esta primera etapa se desarrollarán únicamente las siguientes especificaciones:

- Gestión de Eventos.
- Inscripción de Participantes.

---

# 6. Actores

## Organizador

Responsable de crear, administrar y publicar eventos.

Puede:

- Crear eventos.
- Modificar eventos.
- Cancelar eventos.
- Consultar inscripciones.

---

## Participante

Usuario que accede al sistema para inscribirse en eventos.

Puede:

- Registrarse.
- Consultar eventos.
- Inscribirse.
- Cancelar una inscripción.

---

# 7. Arquitectura prevista

Se proyecta una arquitectura cliente-servidor compuesta por:

Frontend Web

↓

API REST

↓

Base de Datos Relacional

La implementación concreta será definida en futuras etapas del proyecto.

---

# 8. Organización del repositorio

```text
/
│
├── README.md
├── Project.md
├── Contracts.md
│
└── specs/
    ├── gestion-eventos.md
    └── inscripcion-participantes.md
```

Cada archivo dentro del directorio **specs** representa una funcionalidad independiente del sistema.

---

# 9. Metodología de trabajo

El proyecto adopta el enfoque **Spec-Driven Development (SDD)**.

Cada funcionalidad deberá documentarse mediante una Spec que incluya:

1. Objetivo y contexto.
2. Historias de usuario.
3. Requisitos funcionales.
4. Reglas de negocio.
5. Restricciones técnicas.
6. Modelo de datos.
7. Plan de tareas.
8. Estrategia de verificación.

Las Specs deberán respetar las reglas definidas en **Contracts.md**.

---

# 10. Control de versiones

El proyecto utiliza Git como sistema de control de versiones.

Las modificaciones deberán registrarse mediante commits descriptivos y mantenerse sincronizadas con el repositorio remoto.

---

# 11. Criterios generales de calidad

Las especificaciones deberán cumplir los siguientes criterios:

- Claridad.
- Consistencia.
- Ausencia de ambigüedades.
- Trazabilidad.
- Verificabilidad.
- Mantenibilidad.

Cada requisito deberá poder verificarse mediante criterios objetivos.

---

# 12. Planificación

La documentación del proyecto se desarrollará en el siguiente orden:

1. Definición de documentos generales.
2. Elaboración de las Specs.
3. Revisión de consistencia.
4. Verificación de cumplimiento de los requisitos.
5. Publicación de la documentación.

---

# 13. Riesgos identificados

Los principales riesgos considerados para el proyecto son:

- Ambigüedad en los requerimientos.
- Cambios en las reglas de negocio.
- Inconsistencias entre especificaciones.
- Omisión de escenarios de uso.

La utilización de SDD busca reducir estos riesgos mediante una especificación detallada y verificable.

---

# 14. Referencias

- Trabajo Práctico N.º 2 – Ingeniería de Software III.
- Documento **Contracts.md**.
- Especificaciones funcionales ubicadas en el directorio **specs/**.
