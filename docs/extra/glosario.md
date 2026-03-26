# 📚 Glosario de Términos

## Objetivo

Definir los conceptos técnicos clave que aparecen en esta documentación, para que cualquier lector pueda entenderla independientemente de su nivel previo.

---

## Requisitos

No se necesita ningún requisito técnico para consultar esta página. Es una referencia de consulta libre.

---

## Términos

### A

**API (Application Programming Interface)**
Conjunto de reglas que permite que dos aplicaciones se comuniquen entre sí. En este proyecto, el backend se comunica con OpenAI a través de su API enviando mensajes y recibiendo respuestas.

**API Key**
Clave secreta que identifica a un usuario o aplicación ante un servicio externo. En este proyecto se usa para autenticarse ante la API de OpenAI. Nunca debe compartirse ni subirse a repositorios públicos.

---

### B

**Backend**
Parte del sistema que se ejecuta en el servidor y que el usuario no ve directamente. En este proyecto, el backend está hecho con Node.js y Express, y se encarga de recibir mensajes del frontend, llamar a la API de OpenAI y devolver las respuestas.

---

### C

**Chatbot**
Programa informático diseñado para simular una conversación con personas a través de texto. Los chatbots modernos basados en IA generativa como GPT pueden mantener conversaciones contextuales en lenguaje natural.

**Contexto / Historial**
Conjunto de mensajes anteriores de la conversación que se envían a la IA en cada petición para que pueda recordar lo que se ha hablado. Sin historial, el chatbot respondería cada mensaje como si fuera una conversación nueva.

---

### E

**Express.js**
Framework minimalista para Node.js que facilita la creación de servidores web y APIs REST. Es el framework que usa el backend de este proyecto.

**Endpoint**
Ruta específica de una API que acepta peticiones. Por ejemplo, `/api/chat` es el endpoint que recibe los mensajes del usuario y devuelve la respuesta del chatbot.

---

### F

**Frontend**
Parte del sistema que ve y usa el usuario directamente en el navegador. En este proyecto, el frontend es una página HTML sencilla con un campo de texto y un área de conversación.

---

### G

**GPT (Generative Pre-trained Transformer)**
Familia de modelos de lenguaje desarrollados por OpenAI. Son la base del motor de IA de este chatbot. Los modelos GPT son capaces de generar texto coherente y contextualmente relevante en respuesta a una entrada.

---

### J

**JSON (JavaScript Object Notation)**
Formato ligero de intercambio de datos basado en texto, muy usado en APIs web. El frontend y el backend de este proyecto se comunican enviando y recibiendo JSON.

```json
{
  "message": "Hola",
  "history": []
}
```

---

### L

**LLM (Large Language Model)**
Modelo de inteligencia artificial entrenado con enormes cantidades de texto para entender y generar lenguaje natural. GPT-4o es un ejemplo de LLM.

---

### N

**Node.js**
Entorno de ejecución de JavaScript del lado del servidor. Permite usar JavaScript fuera del navegador. Es la tecnología sobre la que se construye el backend de este proyecto.

---

### P

**Prompt**
Texto de entrada que se envía al modelo de IA para obtener una respuesta. En este proyecto hay dos tipos de prompts: el **system prompt** (instrucciones de comportamiento) y el **user prompt** (mensaje del usuario).

**Prompt Engineering**
Técnica de diseño de prompts para obtener respuestas más precisas, seguras o útiles de un modelo de IA. Es la principal forma de personalizar el comportamiento del chatbot sin necesidad de reentrenarlo.

---

### S

**System Prompt**
Instrucciones iniciales que definen la personalidad, el rol y las restricciones del chatbot. El usuario no lo ve, pero condiciona todas las respuestas del modelo.

---

### T

**Token**
Unidad mínima de texto que procesa un modelo de IA. Aproximadamente equivale a ¾ de una palabra en inglés. El coste de uso de la API de OpenAI se mide en tokens consumidos.

---

## Verificación

Si encuentras un término en la documentación que no aparece en este glosario, consulta el [glosario oficial de OpenAI](https://platform.openai.com/docs/introduction) o la [documentación de Node.js](https://nodejs.org/en/docs/).

---

## Errores frecuentes

Confundir **token** con **carácter** es un error habitual. Un token no es un carácter, ni una palabra exacta: es una unidad estadística que varía según el idioma y el contexto. El español consume algo más de tokens que el inglés para el mismo contenido.

---

> 🔗 [Volver al inicio](../index.md) | ❓ [Ver FAQ](../referencia/faq.md)
