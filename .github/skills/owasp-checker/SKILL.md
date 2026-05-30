---
name: owasp-checker
description: "Analiza código en busca de vulnerabilidades del OWASP Top 10 y genera un reporte estructurado de seguridad. Usar siempre que el usuario mencione: auditoría de seguridad, vulnerabilidades, XSS, SQL injection, CSRF, seguridad en PHP, seguridad en JavaScript, revisar seguridad del código, OWASP, exposición de datos, autenticación insegura, o quiera saber si su código es seguro."
---

# OWASP Checker

Analiza código fuente (JavaScript, PHP, HTML) contra las vulnerabilidades del OWASP Top 10 y produce un reporte de seguridad accionable.

El objetivo es identificar riesgos reales y concretos en el código, no solo mencionar categorías abstractas. Cada hallazgo debe incluir el fragmento vulnerable y una corrección específica.

## OWASP Top 10 a revisar

| # | Categoría | Ejemplos concretos a buscar |
|---|---|---|
| A01 | Control de acceso roto | Rutas sin autenticación, IDOR, falta de verificación de roles |
| A02 | Fallos criptográficos | Datos sensibles en texto plano, MD5/SHA1 para contraseñas, HTTP sin TLS |
| A03 | Inyección | SQL injection, XSS, inyección de comandos, eval() con input del usuario |
| A04 | Diseño inseguro | Lógica de negocio que puede ser abusada, falta de rate limiting |
| A05 | Mala configuración | Mensajes de error con stack trace, cabeceras de seguridad faltantes |
| A06 | Componentes vulnerables | Versiones desactualizadas, dependencias sin verificar |
| A07 | Fallos de autenticación | Contraseñas débiles permitidas, sesiones no invalidadas, tokens predecibles |
| A08 | Integridad de datos | Deserialización insegura, actualizaciones sin verificar firma |
| A09 | Falta de logging | Operaciones críticas sin registro, errores silenciados |
| A10 | SSRF | Peticiones a URLs controladas por el usuario sin validar |

## Proceso de análisis

1. Leer el archivo o fragmento proporcionado
2. Para cada vulnerabilidad encontrada, identificar:
   - La categoría OWASP exacta (A01-A10)
   - El fragmento de código afectado (citar líneas)
   - Por qué es un riesgo real en este contexto
   - La corrección concreta con ejemplo de código
3. Clasificar por criticidad: 🔴 alta, 🟡 media, 🟢 baja/informativa
4. Si el código es seguro en alguna categoría, mencionarlo brevemente

## Formato del reporte

### 🔒 Reporte de Seguridad OWASP: `<nombre del archivo>`

**Resumen**: X vulnerabilidades encontradas (X alta, X media, X baja)

---

**🔴 [A03] Inyección — Alta**
```
// Código vulnerable (línea N):
<fragmento exacto>
```
**Riesgo**: [explicación concreta de cómo se puede explotar]
**Corrección**:
```
// Código seguro:
<ejemplo corregido>
```

---

*(repetir para cada hallazgo)*

---

**✅ Sin hallazgos en**: A02, A06 *(mencionar categorías limpias)*

**Veredicto final**: 🔴 Crítico / 🟡 Requiere atención / ✅ Sin vulnerabilidades detectadas
