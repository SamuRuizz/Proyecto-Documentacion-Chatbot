# 🏁 Conclusiones y Próximos Pasos

## Objetivo

Resumir lo aprendido durante el proyecto y proponer una hoja de ruta para seguir mejorando el chatbot más allá de esta documentación.

---

## ¿Qué hemos construido?

A lo largo de este proyecto hemos diseñado e implementado un chatbot conversacional completo basado en inteligencia artificial. El sistema integra tres capas bien diferenciadas:

- Un **frontend web** sencillo y accesible desde cualquier navegador
- Un **backend en Node.js** que actúa como intermediario seguro
- La **API de OpenAI** como motor de generación de lenguaje natural

El resultado es un sistema funcional, personalizable y desplegable en cualquier entorno, desde un portátil en local hasta un servidor en la nube.

---

## Lo que hemos aprendido

| Área | Conceptos clave |
|---|---|
| Inteligencia Artificial | Modelos LLM, tokens, system prompt, prompt engineering |
| Backend | API REST con Express, variables de entorno, gestión de historial |
| Frontend | Comunicación asíncrona con `fetch`, manejo de eventos |
| Buenas prácticas | Seguridad de claves, control de costes, flujo Git |

---

## Limitaciones actuales del proyecto

El chatbot en su estado actual tiene algunas limitaciones conocidas que es importante tener en cuenta:

- **Sin persistencia**: el historial de conversación se pierde al cerrar el navegador
- **Sin autenticación**: cualquier usuario con acceso a la URL puede usar el chatbot
- **Sin límite de uso por usuario**: un solo usuario podría agotar el crédito de la API
- **Dependencia de un proveedor externo**: si OpenAI tiene una interrupción, el chatbot deja de funcionar

---

## Próximos pasos recomendados

### Nivel básico

1. Personalizar el system prompt para un caso de uso concreto ([ver ejemplos](extra/casos-de-uso.md))
2. Ajustar el modelo y los tokens según las necesidades ([ver comparativa](extra/comparativa-modelos.md))
3. Desplegar el chatbot en una plataforma cloud gratuita como [Railway](https://railway.app/) o [Render](https://render.com/)

### Nivel intermedio

1. Añadir una base de datos para persistir el historial de conversaciones
2. Implementar un sistema de autenticación básico con tokens JWT
3. Añadir un límite de peticiones por IP para evitar abusos

### Nivel avanzado

1. Explorar [Function Calling](https://platform.openai.com/docs/guides/function-calling) para conectar el chatbot con servicios externos
2. Evaluar modelos open source como [Mistral](https://mistral.ai/) o [LLaMA](https://llama.meta.com/) como alternativa a OpenAI
3. Implementar un panel de administración para monitorizar el uso y los costes en tiempo real

---

## Reflexión final

Los chatbots con IA generativa han pasado de ser una tecnología experimental a una herramienta práctica y accesible. Con relativamente poco código y una clave de API, cualquier desarrollador puede construir un asistente conversacional útil y personalizado.

El verdadero valor no está en la tecnología en sí, sino en **cómo se configura y adapta** a las necesidades reales de los usuarios. El prompt engineering, la elección del modelo y el diseño de la experiencia de usuario son las claves que marcan la diferencia entre un chatbot genérico y uno realmente útil.

---

> 🔗 [Volver al inicio](index.md) | 🔒 [Ver seguridad y buenas prácticas](seguridad.md)
