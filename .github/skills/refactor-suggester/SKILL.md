---
name: refactor-suggester
description: "Propone refactorizaciones concretas con ejemplos de código antes/después. Usar siempre que el usuario mencione: refactorizar, mejorar el código, clean code, código duplicado, función muy larga, código difícil de leer, separar responsabilidades, mejorar legibilidad, simplificar, optimizar estructura del código, code smell, deuda técnica."
---

# Refactor Suggester

Analiza código (JavaScript, PHP, HTML, CSS) y propone refactorizaciones concretas que mejoran legibilidad, mantenibilidad y estructura, respetando las convenciones del proyecto.

El valor está en los ejemplos: cada sugerencia debe mostrar el código actual y cómo quedaría después de aplicar el cambio. No se trata de reescribir todo — sino de identificar los puntos donde un cambio pequeño tiene el mayor impacto.

## Convenciones del proyecto a respetar

- **JavaScript**: camelCase, 2 espacios de indentación, soluciones nativas
- **PHP**: snake_case, 2 espacios de indentación, sin dependencias innecesarias
- **General**: funciones con una sola responsabilidad, nombres descriptivos, comentarios solo donde aporten valor

## Patrones a detectar

**Complejidad innecesaria**
- Funciones que hacen más de una cosa
- Condicionales anidados que pueden aplanarse
- Código repetido que puede extraerse

**Naming**
- Variables o funciones con nombres genéricos (`data`, `temp`, `doStuff`)
- Nombres que no reflejan el propósito real

**Estructura**
- Funciones demasiado largas (más de 20-30 líneas como señal de alerta)
- Lógica mezclada con presentación (en PHP/HTML)
- Callbacks anidados en JS que pueden simplificarse con promesas o async/await

**Legibilidad**
- Expresiones booleanas complejas que pueden extraerse a una variable con nombre
- Números mágicos sin contexto
- Comentarios que explican "qué" en vez de "por qué"

## Proceso

1. Leer el código proporcionado
2. Identificar los 3-5 cambios con mayor impacto (no listar todo lo menor)
3. Para cada uno, mostrar antes/después con una explicación breve del beneficio
4. Priorizar por impacto: 🔵 alto impacto, ⚪ mejora menor

## Formato de salida

### ♻️ Sugerencias de Refactorización: `<nombre del archivo>`

---

**🔵 [Tipo de mejora]: [título descriptivo]**

Antes:
```js
// código actual
```
Después:
```js
// código refactorizado
```
**Por qué**: [beneficio concreto en 1-2 líneas]

---

*(repetir para cada sugerencia)*

**Resumen**: X cambios sugeridos. Aplicarlos todos mejoraría [legibilidad / mantenibilidad / rendimiento].

## Ejemplo de análisis

**🔵 Extraer condicional complejo a variable con nombre**

Antes:
```js
if (user.age >= 18 && user.active && !user.banned) {
  // ...
}
```
Después:
```js
const canAccess = user.age >= 18 && user.active && !user.banned;
if (canAccess) {
  // ...
}
```
**Por qué**: El condicional ahora tiene un nombre que explica su intención, facilitando la lectura y el testing futuro.
