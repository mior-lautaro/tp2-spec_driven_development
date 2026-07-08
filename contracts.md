# Contracts.md

# Contratos Generales del Proyecto

## Información general

**Proyecto:** Software de Organización y Gestión de Eventos Académicos

**Versión:** 1.0


---

# Objetivo

Este documento establece las reglas, convenciones y contratos generales que deberán respetar todas las especificaciones (Specs) del proyecto.

Su finalidad es garantizar consistencia entre módulos, facilitar el desarrollo futuro y evitar ambigüedades durante la implementación.

---

# Convenciones generales

## Idioma

- Toda la documentación se redactará en español.
- Los nombres técnicos podrán mantenerse en inglés cuando sea una convención ampliamente aceptada (por ejemplo: API, UUID, REST).

---

## Convenciones de nombres

### Variables

camelCase

Ejemplo:

```
fechaInicio
fechaLimiteInscripcion
cupoMaximo
```

### Clases / Entidades

PascalCase

Ejemplo:

```
Evento
Participante
Inscripcion
```

### Archivos

kebab-case

Ejemplo

```
gestion-eventos.md
inscripcion-participantes.md
```

---

# Identificadores

Todas las entidades del sistema deberán poseer un identificador único.

Ejemplo:

```
id
```

Este identificador será inmutable durante toda la vida útil del registro.

---

# Manejo de fechas

Todas las fechas deberán almacenarse utilizando el estándar ISO 8601.

Ejemplo:

```
2026-08-15
```

No se utilizarán formatos dependientes de la configuración regional.

---

# Estados

Las entidades deberán utilizar estados claramente definidos.

## Evento

Estados posibles:

- Borrador
- Publicado
- Finalizado
- Cancelado

## Inscripción

Estados posibles:

- Pendiente
- Confirmada
- Cancelada

---

# Reglas generales de negocio

## Eventos

- Todo evento debe poseer un nombre.
- Todo evento debe poseer una fecha de inicio.
- La fecha de finalización no podrá ser anterior a la fecha de inicio.
- El cupo máximo deberá ser mayor que cero.
- La fecha límite de inscripción deberá ser anterior al inicio del evento.

---

## Participantes

- Un participante podrá registrarse una única vez mediante su correo electrónico.
- El correo electrónico deberá ser único dentro del sistema.

---

## Inscripciones

- Un participante no podrá inscribirse más de una vez al mismo evento.
- No se permitirán inscripciones cuando el período de inscripción haya finalizado.
- No se permitirán inscripciones cuando el cupo máximo haya sido alcanzado.

---

# Validaciones

Toda información recibida deberá validarse antes de ser persistida.

Como mínimo:

- Campos obligatorios.
- Longitud máxima.
- Formato de correo electrónico.
- Fechas válidas.
- Valores numéricos positivos.

---

# Manejo de errores

Toda operación fallida deberá devolver:

- código del error
- descripción del error

Los mensajes deberán ser claros y comprensibles para el usuario.

---

# Auditoría

Las operaciones críticas deberán poder ser auditadas.

Como mínimo:

- creación de eventos
- modificación de eventos
- cancelación de eventos
- inscripción de participantes
- cancelación de inscripciones

---

# Seguridad

El sistema deberá contemplar autenticación para las operaciones privadas.

Las operaciones públicas únicamente permitirán:

- consultar eventos
- visualizar información pública

Las operaciones de administración requerirán autenticación.

---

# Compatibilidad entre Specs

Todas las Specs deberán respetar este documento.

En caso de conflicto entre una Spec y este documento, prevalecerá lo definido en Contracts.md.

Las nuevas reglas generales deberán incorporarse únicamente en este documento para mantener la consistencia del proyecto.
