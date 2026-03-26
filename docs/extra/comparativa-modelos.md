# 📊 Comparativa de Modelos de IA

## Objetivo

Comparar los modelos de OpenAI disponibles para elegir el más adecuado según el caso de uso, el presupuesto y la calidad de respuesta necesaria.

---

## Requisitos

- Cuenta en [OpenAI Platform](https://platform.openai.com/)
- Conocimiento básico del fichero `.env` del proyecto

---

## Modelos disponibles

| Modelo | Velocidad | Calidad | Coste (aprox.) | Recomendado para |
|---|---|---|---|---|
| `gpt-4o-mini` | ⚡⚡⚡ Muy rápido | ⭐⭐⭐ Buena | Muy bajo | Proyectos de prueba, alto volumen |
| `gpt-4o` | ⚡⚡ Rápido | ⭐⭐⭐⭐⭐ Excelente | Medio-alto | Producción, respuestas complejas |
| `gpt-3.5-turbo` | ⚡⚡⚡ Muy rápido | ⭐⭐ Aceptable | Mínimo | Pruebas rápidas, presupuesto cero |

---

## ¿Cómo cambiar el modelo?

Edita el fichero `.env` en la raíz del proyecto:

```bash
# Opción económica (recomendada para empezar)
OPENAI_MODEL=gpt-4o-mini

# Opción de máxima calidad
OPENAI_MODEL=gpt-4o

# Opción mínima para pruebas
OPENAI_MODEL=gpt-3.5-turbo
```

No es necesario reiniciar el servidor si usas `npm run dev` (nodemon lo hace automáticamente).

---

## Comparativa por caso de uso

### ¿Cuándo usar `gpt-4o-mini`?

- Chatbot de soporte con preguntas simples y repetitivas
- Proyectos educativos o personales con presupuesto limitado
- Alto volumen de mensajes donde el coste importa

### ¿Cuándo usar `gpt-4o`?

- El chatbot necesita razonar sobre problemas complejos
- Se requieren respuestas muy detalladas o con código avanzado
- La calidad de la experiencia de usuario es prioritaria sobre el coste

### ¿Cuándo usar `gpt-3.5-turbo`?

- Solo para pruebas rápidas de concepto
- Cuando el presupuesto es prácticamente cero
- Tareas muy simples donde la calidad es secundaria

---

## Prueba de comparación rápida

Puedes comparar los modelos enviando el mismo mensaje a cada uno:

```bash
# Cambia el modelo en .env y ejecuta:
curl -X POST http://localhost:3000/api/chat \
  -H "Content-Type: application/json" \
  -d '{"message": "Explica qué es una API REST en 3 frases", "history": []}'
```

Repite el comando cambiando `OPENAI_MODEL` en `.env` para comparar la calidad y velocidad de cada respuesta.

---

## Verificación

Tras cambiar el modelo en `.env`, comprueba en los logs del servidor que el modelo correcto se está usando:

```
POST /api/chat — modelo: gpt-4o-mini — tokens: 87 — 340ms
```

---

## Errores frecuentes

Si el modelo que especificas en `.env` no existe o está mal escrito, la API de OpenAI devolverá un error `404 model not found`. Consulta siempre la [lista actualizada de modelos disponibles](https://platform.openai.com/docs/models) en la documentación oficial.

---

> 🔗 [Volver al inicio](../index.md) | 📖 [Ver glosario de términos](glosario.md)
