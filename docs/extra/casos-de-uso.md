# 🧩 Casos de Uso Reales

## Objetivo

Mostrar situaciones concretas en las que un chatbot con IA aporta valor real, con ejemplos de configuración para cada escenario.

---

## Requisitos

- Chatbot instalado y funcionando ([ver Quickstart](../guia/quickstart.md))
- Conocimientos básicos de edición del system prompt

---

## Caso 1 — Soporte técnico para una tienda online

Una tienda online recibe decenas de preguntas repetidas al día: horarios, devoluciones, estado de pedidos. Un chatbot puede responder el 80% de estas consultas sin intervención humana.

**Configuración del system prompt:**

```javascript
const systemPrompt = `
  Eres el asistente de soporte de TiendaEjemplo.
  Solo respondes preguntas sobre: pedidos, devoluciones, 
  métodos de pago y horarios de atención.
  Si no sabes la respuesta, deriva al email soporte@tienda.com.
  Responde siempre en un tono amable y profesional.
`;
```

**Métricas esperadas:**

| Métrica | Sin chatbot | Con chatbot |
|---|---|---|
| Tiempo medio de respuesta | 4 horas | < 10 segundos |
| Consultas resueltas sin agente | 20% | ~75% |
| Coste por consulta | Alto | Muy bajo |

---

## Caso 2 — Asistente de aprendizaje para estudiantes

Un chatbot configurado como tutor puede ayudar a estudiantes a resolver dudas sobre una asignatura concreta, explicar conceptos y proponer ejercicios.

**Configuración del system prompt:**

```javascript
const systemPrompt = `
  Eres un tutor de programación web para estudiantes de DAW.
  Explica los conceptos con ejemplos de código simples.
  Si el estudiante comete un error, guíale hacia la solución 
  en lugar de dársela directamente.
  Usa un lenguaje cercano y motivador.
`;
```

---

## Caso 3 — Asistente interno para equipos de desarrollo

Un chatbot interno puede ayudar al equipo a consultar documentación, convenciones de código o procedimientos sin salir del entorno de trabajo.

**Ejemplo de flujo:**

```
Desarrollador: "¿Cuál es nuestra convención para nombrar ramas en Git?"
Chatbot: "Usamos el prefijo feature/ para nuevas funcionalidades,
          fix/ para correcciones y docs/ para documentación.
          Ejemplo: feature/login-oauth"
```

---

## Verificación

Para cada caso de uso, verifica que el system prompt funciona correctamente enviando al menos 5 preguntas representativas del escenario y comprobando que las respuestas son coherentes con la configuración.

---

## Errores frecuentes

El error más común al adaptar el chatbot a un caso de uso concreto es un system prompt demasiado vago. Cuanto más específico y detallado sea, más predecible y útil será el comportamiento del chatbot.

---

> 🔗 [Volver al inicio](../index.md) | 📊 [Ver comparativa de modelos](comparativa-modelos.md)
