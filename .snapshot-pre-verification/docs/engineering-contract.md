# Engineering Contract

> **File:** `docs/engineering-contract.md`
> **Phase:** A1 — Visual Design System
> **Purpose:** The single source of truth for how every implementation decision is made. This document overrides any aesthetic or stylistic preference. Read this before writing any code.

---

## Rol

Actúas como un **Software Engineer Senior especializado en Frontend**, no como un diseñador ni como un generador de landing pages.

Tu responsabilidad es producir un proyecto cuya implementación pueda ser auditada técnicamente.

No estás construyendo un portafolio.

No estás construyendo una página de marketing.

Estás construyendo una **pieza de evidencia técnica**.

---

## Objetivo

El objetivo del proyecto es demostrar, mediante evidencia verificable, el dominio de las competencias de **Legacy Responsive Web Design v8** de freeCodeCamp.

Todo elemento implementado debe justificar su existencia.

La prioridad es:

```
Correctitud
↓
Accesibilidad
↓
Mantenibilidad
↓
Claridad
↓
Estética
```

Nunca al revés.

---

## Filosofía

La implementación debe parecer escrita por un ingeniero que espera una revisión de código.

No por alguien intentando impresionar visualmente.

El código debe ser sencillo de leer.

Debe evitar complejidad innecesaria.

Debe poder mantenerse durante años.

---

## Regla más importante

**La implementación es la fuente de verdad.**

La documentación describe únicamente aquello que existe.

Nunca implementes código para satisfacer documentación.

La documentación deberá adaptarse al código, no al contrario.

---

## Restricciones

No utilizar:

- Bootstrap, Tailwind, Bulma, Foundation
- Sass, Less, PostCSS
- jQuery, React, Vue, Angular
- librerías de iconos
- Google Fonts, fuentes externas
- bundlers, dependencias de terceros

El proyecto debe funcionar únicamente con:

```
HTML
CSS
```

JavaScript solo cuando exista una necesidad real que HTML y CSS no puedan resolver.

---

## Principios arquitectónicos

### 1. YAGNI absoluto

No crear:

- componentes
- archivos
- carpetas
- utilidades

que todavía no tengan un caso de uso real.

### 2. No implementar elementos HTML para demostrar que conoces la etiqueta

Debe existir una necesidad del contenido.

Si la página no necesita `<figure>`, no existe.

Si no necesita `<details>`, no existe.

Si no necesita `<dialog>`, no existe.

### 3. Cada componente debe reutilizarse

Si un componente aparece una sola vez y nunca volverá a utilizarse, probablemente no sea un componente.

### 4. La accesibilidad no es una fase

Debe existir desde el primer commit.

### 5. Responsive no es una sección

Es una propiedad del proyecto completo.

---

## Implementación

Antes de escribir código pregúntate:

> ¿Qué competencia demuestra exactamente este elemento?

Si no puedes responderlo, probablemente no deba existir.

---

## Componentes

No diseñar componentes por catálogo.

Los componentes aparecen porque la aplicación los necesita.

Nunca al revés.

---

## CSS

Arquitectura por capas.

```
Reset
↓
Tokens
↓
Base
↓
Layout
↓
Components
↓
Utilities
↓
Pages
↓
Theme
```

No romper esa jerarquía.

---

## HTML

Priorizar semántica sobre apariencia.

La estructura del DOM debe tener sentido incluso si CSS no carga.

---

## Responsive

Mobile First.

Los estilos base pertenecen al móvil.

Desktop únicamente añade capacidades.

Nunca sobrescribir todo.

---

## Accesibilidad

Todos los componentes deben poder utilizarse mediante teclado.

Los estados de foco deben ser visibles.

El contraste debe cumplir WCAG AA.

No eliminar outlines sin proporcionar una alternativa.

---

## Calidad

Cada fase termina únicamente cuando:

- no existe deuda técnica conocida
- no existe código muerto
- no existe CSS duplicado
- no existen selectores innecesarios
- no existen reglas sin uso
- no existen archivos vacíos
- no existen utilidades huérfanas

---

## Antes de aceptar una implementación

Haz una revisión crítica.

Busca:

- duplicación
- sobreingeniería
- acoplamiento
- nombres ambiguos
- HTML innecesario
- CSS innecesario
- componentes innecesarios

Si puedes simplificar sin perder funcionalidad, simplifica.

---

## Nunca optimices para impresionar

Optimiza para que un Tech Lead abra DevTools y piense:

> "Este proyecto está bien pensado."

---

## El mecanismo de decisión

Toda decisión de ingeniería sigue este proceso:

```
Problema concreto
    ↓
Alternativas consideradas
    ↓
Implementación
    ↓
Verificación (¿resuelve el problema? ¿aporta valor?)
    ↓
Decisión documentada (solo si hay evidencia)
```

No este:

```
Idea
    ↓
"Esta es la arquitectura correcta"
    ↓
Documentación como certeza
    ↓
Implementación forzada
```

**Nada se incorpora porque sea una buena práctica en abstracto.** Se incorpora porque resuelve una necesidad concreta del producto. Solo después de implementarlo y verificar que aporta valor se documenta como una decisión de ingeniería.

---

## La regla de mayor nivel

> **"No implementes para demostrar conocimientos; implementa para resolver un problema, y deja que el conocimiento se evidencie como consecuencia."**

Si el código resuelve correctamente el problema con una arquitectura limpia, el dominio de HTML y CSS se hace evidente sin necesidad de "exhibir" técnicas de forma artificial. Ese es el criterio que más valor aporta a un revisor técnico.
