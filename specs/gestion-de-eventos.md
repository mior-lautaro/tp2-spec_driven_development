# Spec - Gestión de Eventos

**Código:** SPEC-001

**Versión:** 1.0

**Estado:** Aprobada

---

# 1. Objetivo y Contexto

## Objetivo

El módulo de Gestión de Eventos tiene como objetivo permitir a los organizadores crear, administrar y publicar eventos académicos dentro de la plataforma.

Este módulo constituye el núcleo funcional del sistema, ya que el resto de las funcionalidades (inscripciones, acreditaciones, certificados, informes y encuestas) dependen de la existencia de un evento previamente definido.

## Contexto

La plataforma está destinada a la organización de eventos académicos como:

- Congresos
- Jornadas
- Cursos
- Seminarios
- Talleres
- Charlas

Cada evento deberá almacenar la información necesaria para que posteriormente los participantes puedan consultarlo e inscribirse.

El módulo deberá respetar las reglas generales definidas en **Contracts.md** y la arquitectura establecida en **Project.md**.

---

# 2. Historias de Usuario y Criterios de Aceptación

## HU-001 - Crear evento

**Como** organizador

**Quiero** registrar un nuevo evento

**Para** publicarlo posteriormente en la plataforma.

### Criterios de aceptación

- Debe permitir ingresar toda la información obligatoria.
- El evento deberá almacenarse únicamente si supera todas las validaciones.
- El sistema deberá informar el resultado de la operación.

---

## HU-002 - Modificar evento

**Como** organizador

**Quiero** modificar un evento existente

**Para** mantener actualizada su información.

### Criterios

- Debe conservar el identificador original.
- Deben validarse nuevamente todas las reglas de negocio.

---

## HU-003 - Publicar evento

**Como** organizador

**Quiero** publicar un evento

**Para** que sea visible para los participantes.

### Criterios

- Sólo podrán publicarse eventos válidos.
- Los eventos publicados aparecerán en el listado público.

---

## HU-004 - Consultar eventos

**Como** participante

**Quiero** visualizar los eventos disponibles

**Para** decidir en cuál inscribirme.

### Criterios

- Deben mostrarse únicamente eventos publicados.
- Debe permitirse filtrar por tipo y fecha.

---

# 3. Requisitos Funcionales y Reglas de Negocio

## Requisitos funcionales

RF-001 Crear evento.

RF-002 Modificar evento.

RF-003 Eliminar evento.

RF-004 Publicar evento.

RF-005 Consultar eventos.

RF-006 Filtrar eventos por tipo.

RF-007 Filtrar eventos por fecha.

RF-008 Consultar el detalle de un evento.

---

## Reglas de negocio

RN-001 Todo evento debe poseer un nombre.

RN-002 La fecha de finalización no puede ser anterior a la fecha de inicio.

RN-003 El cupo máximo debe ser mayor que cero.

RN-004 La fecha límite de inscripción debe ser anterior al inicio del evento.

RN-005 No podrá modificarse un evento ya finalizado.

RN-006 Sólo podrán publicarse eventos completos y válidos.

---

# 4. Restricciones técnicas específicas

- Arquitectura REST.
- Comunicación mediante JSON.
- Persistencia en base de datos relacional.
- Fechas bajo estándar ISO-8601.
- Identificadores UUID.
- Todas las operaciones deberán registrar auditoría.

---

# 5. Modelo de datos

## Entidad Evento

| Campo | Tipo | Obligatorio |
|---------|------|-------------|
| id | UUID | Sí |
| nombre | String | Sí |
| descripcion | Text | Sí |
| tipo | Enum | Sí |
| fechaInicio | Date | Sí |
| fechaFin | Date | Sí |
| fechaLimiteInscripcion | Date | Sí |
| cupoMinimo | Integer | No |
| cupoMaximo | Integer | Sí |
| estado | Enum | Sí |

Estados posibles:

- Borrador
- Publicado
- Finalizado
- Cancelado

---

# 6. Plan de Tareas

- Diseñar entidad Evento.
- Implementar validaciones.
- Implementar creación.
- Implementar modificación.
- Implementar publicación.
- Implementar consulta.
- Implementar filtros.
- Implementar auditoría.
- Realizar pruebas funcionales.

---

# 7. Estrategia de Verificación

Se verificará:

- Creación correcta.
- Fechas inválidas.
- Cupo inválido.
- Publicación correcta.
- Consulta pública.
- Funcionamiento de filtros.
- Persistencia de datos.
- Cumplimiento de reglas de negocio.
