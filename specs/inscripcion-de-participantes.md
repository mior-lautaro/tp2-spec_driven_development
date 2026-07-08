# Spec - Inscripción de Participantes

**Código:** SPEC-002

**Versión:** 1.0

**Estado:** Aprobada

---

# 1. Objetivo y Contexto

## Objetivo

El módulo de Inscripción de Participantes tiene como objetivo permitir que los usuarios se registren en eventos académicos publicados, administrando el proceso de inscripción de acuerdo con las reglas de negocio establecidas por la organización del evento.

Este módulo debe garantizar la integridad de las inscripciones, respetando las restricciones de cupo, fechas de inscripción y unicidad de los registros.

## Contexto

Una vez que un organizador publica un evento, los participantes pueden consultar su información e inscribirse dentro del período habilitado.

Cada inscripción vincula un participante con un evento determinado y registra el estado de dicha inscripción.

Este módulo depende de la existencia de eventos creados mediante la Spec "Gestión de Eventos" y deberá respetar los lineamientos definidos en **Project.md** y **Contracts.md**.

---

# 2. Historias de Usuario y Criterios de Aceptación

## HU-005 - Registrarse en la plataforma

**Como** usuario

**Quiero** crear una cuenta

**Para** poder inscribirme en eventos académicos.

### Criterios de aceptación

- El correo electrónico debe ser único.
- Todos los campos obligatorios deben completarse.
- La cuenta debe quedar registrada correctamente.

---

## HU-006 - Inscribirse a un evento

**Como** participante

**Quiero** inscribirme en un evento publicado

**Para** reservar mi participación.

### Criterios de aceptación

- El evento debe encontrarse publicado.
- La inscripción debe realizarse dentro del período permitido.
- Debe existir disponibilidad de cupos.
- El sistema debe confirmar la inscripción realizada.

---

## HU-007 - Cancelar una inscripción

**Como** participante

**Quiero** cancelar mi inscripción

**Para** desistir de asistir al evento.

### Criterios de aceptación

- La inscripción debe existir.
- La cancelación debe quedar registrada.
- El cupo deberá liberarse automáticamente.

---

## HU-008 - Consultar mis inscripciones

**Como** participante

**Quiero** visualizar mis inscripciones

**Para** conocer el estado de cada una.

### Criterios de aceptación

- Deben mostrarse únicamente las inscripciones del usuario autenticado.
- Debe visualizarse el estado de cada inscripción.

---

# 3. Requisitos Funcionales y Reglas de Negocio

## Requisitos funcionales

RF-001 Registrar participante.

RF-002 Autenticar participante.

RF-003 Inscribirse a un evento.

RF-004 Cancelar inscripción.

RF-005 Consultar inscripciones personales.

RF-006 Consultar el estado de una inscripción.

RF-007 Validar disponibilidad de cupos.

RF-008 Validar período de inscripción.

---

## Reglas de negocio

RN-001 Un participante podrá registrarse una única vez utilizando su dirección de correo electrónico.

RN-002 Un participante no podrá inscribirse más de una vez al mismo evento.

RN-003 Sólo podrán realizarse inscripciones en eventos publicados.

RN-004 No podrán realizarse inscripciones fuera del período habilitado.

RN-005 No podrán realizarse inscripciones cuando el cupo máximo haya sido alcanzado.

RN-006 La cancelación de una inscripción deberá liberar automáticamente el cupo correspondiente.

RN-007 Toda inscripción deberá quedar asociada exactamente a un participante y a un evento.

RN-008 El historial de inscripciones deberá conservarse para fines administrativos.

---

# 4. Restricciones técnicas específicas del módulo

- El acceso a las operaciones privadas requerirá autenticación.
- Todas las comunicaciones utilizarán formato JSON.
- Los identificadores serán UUID.
- Las fechas utilizarán el estándar ISO-8601.
- Todas las operaciones críticas deberán registrarse para auditoría.
- Las validaciones deberán realizarse tanto en el cliente como en el servidor.

---

# 5. Modelo de Datos

## Entidad Participante

| Campo | Tipo | Obligatorio |
|--------|------|-------------|
| id | UUID | Sí |
| nombre | String | Sí |
| apellido | String | Sí |
| email | String | Sí |
| contraseña | String | Sí |

---

## Entidad Inscripción

| Campo | Tipo | Obligatorio |
|--------|------|-------------|
| id | UUID | Sí |
| participanteId | UUID | Sí |
| eventoId | UUID | Sí |
| fechaInscripcion | DateTime | Sí |
| estado | Enum | Sí |

Estados posibles:

- Pendiente
- Confirmada
- Cancelada

---

## Relaciones

Un participante puede poseer múltiples inscripciones.

Un evento puede poseer múltiples participantes.

Cada inscripción representa la relación entre un único participante y un único evento.

---

# 6. Plan de Tareas

1. Diseñar las entidades Participante e Inscripción.
2. Implementar el registro de participantes.
3. Implementar autenticación.
4. Implementar la inscripción a eventos.
5. Validar cupos disponibles.
6. Validar fechas de inscripción.
7. Implementar cancelación de inscripciones.
8. Implementar consulta de inscripciones.
9. Incorporar auditoría de operaciones.
10. Ejecutar pruebas funcionales y de integración.

---

# 7. Estrategia de Verificación

Se verificará el correcto funcionamiento de los siguientes escenarios:

## Registro

- Registro exitoso.
- Correo electrónico duplicado.
- Datos obligatorios incompletos.

## Inscripción

- Inscripción válida.
- Evento inexistente.
- Evento no publicado.
- Evento sin cupos disponibles.
- Inscripción fuera del período permitido.
- Participante previamente inscripto.

## Cancelación

- Cancelación exitosa.
- Cancelación de una inscripción inexistente.
- Liberación correcta del cupo.

## Consulta

- Visualización de todas las inscripciones del participante.
- Visualización correcta del estado de cada inscripción.

## Integridad

- Verificación de la relación entre Participante, Evento e Inscripción.
- Cumplimiento de todas las reglas de negocio definidas para el módulo.
