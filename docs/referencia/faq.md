# ❓ Preguntas Frecuentes (FAQ)

## Objetivo

Resolver las dudas más comunes sobre el chatbot, su configuración, costes y limitaciones.

---

## Preguntas generales

<details>
<summary>1. ¿Es gratuito usar el chatbot?</summary>

El código del chatbot es **gratuito y de código abierto**. Sin embargo, el chatbot utiliza la [API de OpenAI](https://platform.openai.com/), que tiene un coste por uso basado en el número de tokens procesados.

OpenAI ofrece créditos gratuitos al registrarse, suficientes para pruebas. Para producción, consulta su [página de precios](https://openai.com/api/pricing/).

</details>

<details>
<summary>2. ¿Qué modelo de IA usa el chatbot por defecto?</summary>

Por defecto se usa **`gpt-4o-mini`**, que ofrece un buen equilibrio entre calidad de respuestas y coste. Puedes cambiarlo en el fichero `.env`:

```bash
# Modelos disponibles (de menor a mayor coste)
OPENAI_MODEL=gpt-4o-mini   # Recomendado para pruebas
OPENAI_MODEL=gpt-4o        # Mayor calidad, más caro
OPENAI_MODEL=gpt-3.5-turbo # Más antiguo, muy económico
```

Consulta la lista completa en la [documentación de modelos de OpenAI](https://platform.openai.com/docs/models).

</details>

<details>
<summary>3. ¿El chatbot recuerda las conversaciones anteriores entre sesiones?</summary>

**No por defecto.** El historial de conversación se almacena en la memoria del navegador durante la sesión activa. Al cerrar o recargar la página, el historial se pierde.

Para añadir persistencia, se necesitaría una base de datos (por ejemplo, MongoDB o PostgreSQL) y asociar cada historial a un usuario identificado.

</details>

<details>
<summary>4. ¿Puedo cambiar el idioma del chatbot?</summary>

Sí. El idioma del chatbot depende del **system prompt** configurado en `server.js`. Para forzar respuestas en un idioma concreto:

```javascript
const systemPrompt = `
  Responde siempre en español, independientemente del idioma 
  en que el usuario escriba.
`;
```

</details>

---

## Preguntas técnicas

<details>
<summary>5. ¿Puedo desplegar el chatbot en un servidor en la nube?</summary>

Sí. El chatbot es una aplicación Node.js estándar compatible con cualquier plataforma cloud. Algunas opciones populares:

| Plataforma | Plan gratuito | Dificultad |
|---|---|---|
| [Railway](https://railway.app/) | ✅ Sí | Baja |
| [Render](https://render.com/) | ✅ Sí | Baja |
| [Fly.io](https://fly.io/) | ✅ Sí | Media |
| AWS / GCP / Azure | ❌ De pago | Alta |

Para el despliegue, recuerda configurar las variables de entorno en la plataforma (no subas el fichero `.env` a Git).

</details>

<details>
<summary>6. ¿Cómo protejo mi clave de API de OpenAI?</summary>

Sigue estas buenas prácticas:

- **Nunca** la subas a un repositorio público (Git ignorará `.env` si lo añades a `.gitignore`)
- Usa **variables de entorno del sistema** en producción, no ficheros `.env`
- Establece **límites de gasto** en el panel de OpenAI para evitar facturas inesperadas
- **Rota la clave** periódicamente o si sospechas que está comprometida

```bash
# Asegúrate de que .gitignore incluye .env
echo ".env" >> .gitignore
git rm --cached .env  # Si ya la subiste por error
```

</details>

<details>
<summary>7. ¿Qué son los "tokens" y cómo afectan al coste?</summary>

Un **token** es aproximadamente ¾ de una palabra en inglés (o algo menos en español). Cada llamada a la API de OpenAI consume tokens tanto del mensaje enviado como de la respuesta recibida.

Ejemplo orientativo con `gpt-4o-mini`:

| Acción | Tokens aprox. | Coste aprox. |
|---|---|---|
| Mensaje corto + respuesta | ~200 tokens | ~$0.00003 |
| Conversación larga (10 turnos) | ~2.000 tokens | ~$0.0003 |
| 1.000 conversaciones largas | ~2M tokens | ~$0.30 |

Puedes controlar el gasto con la variable `MAX_TOKENS` en `.env`.

</details>

<details>
<summary>8. ¿El chatbot puede acceder a internet o a mis ficheros?</summary>

**No por defecto.** El modelo GPT de OpenAI solo trabaja con el texto que le envías en la conversación. No puede:

- Navegar por internet en tiempo real
- Acceder a tu sistema de ficheros
- Consultar bases de datos externas

Para añadir estas capacidades, OpenAI ofrece [Function Calling](https://platform.openai.com/docs/guides/function-calling) y herramientas como la búsqueda web en determinados modelos.

</details>

<details>
<summary>9. ¿Puedo usar este chatbot para un negocio o aplicación comercial?</summary>

Sí, siempre que cumplas con los [Términos de uso de OpenAI](https://openai.com/policies/usage-policies/). Algunas consideraciones:

- Informa a tus usuarios de que están interactuando con una IA
- No uses el chatbot para generar contenido engañoso o dañino
- Revisa las políticas de privacidad respecto al tratamiento de datos de usuarios

</details>

<details>
<summary>10. ¿Cómo limito los temas sobre los que puede hablar el chatbot?</summary>

Usa el **system prompt** para restringir el comportamiento:

```javascript
const systemPrompt = `
  Eres un asistente especializado ÚNICAMENTE en soporte técnico 
  de software. Si el usuario pregunta sobre otros temas, 
  indícale amablemente que solo puedes ayudar con tecnología.
`;
```

Esta técnica se llama **prompt engineering** y es la forma principal de personalizar el comportamiento del modelo sin necesidad de entrenarlo.

</details>

---

## Verificación

Si sigues teniendo problemas tras consultar esta FAQ:

1. Revisa los [errores frecuentes de Quickstart](../guia/quickstart.md#errores-frecuentes)
2. Revisa los [errores frecuentes de Instalación](../guia/instalacion.md#errores-frecuentes)
3. Consulta los [logs del servidor](#verificación) con `npm run dev` (muestra más detalles)

---

## Errores frecuentes

<details>
<summary>❌ No encuentro la respuesta a mi pregunta en esta FAQ</summary>

Puedes consultar recursos adicionales:

- [Foro de la comunidad de OpenAI](https://community.openai.com/)
- [Stack Overflow — etiqueta openai-api](https://stackoverflow.com/questions/tagged/openai-api)
- [Documentación oficial de OpenAI](https://platform.openai.com/docs)

</details>

---

> 🏠 [Volver al inicio](../index.md) | 💻 [Ver referencia de comandos](comandos.md)
