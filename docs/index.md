# 🤖 ChatBot con Inteligencia Artificial

> **Documentación técnica completa** para el diseño, implementación y despliegue de un chatbot potenciado por IA generativa.

---

## ¿Qué es este proyecto?

Este proyecto documenta la creación de un **chatbot conversacional** basado en inteligencia artificial, capaz de responder preguntas, dar soporte a usuarios y mantener conversaciones contextuales en lenguaje natural.

El sistema se apoya en tres pilares:

- **API de IA** (OpenAI GPT) como motor de generación de respuestas
- **Backend en Node.js** como servidor intermediario y gestor de sesiones
- **Frontend web** como interfaz de usuario sencilla y accesible

---

## Vista rápida del sistema

```
Usuario  ──►  Frontend (HTML/JS)
                    │
                    ▼
             Backend (Node.js)
                    │
                    ▼
             API de OpenAI  ──►  Respuesta GPT
                    │
                    ▼
             Frontend  ──►  Usuario
```

---

## Navegación del sitio

| Sección | Descripción | Enlace |
|---|---|---|
| 🚀 Quickstart | Arranca el chatbot en minutos | [Ir a Quickstart](guia/quickstart.md) |
| 🔧 Instalación | Guía detallada de instalación | [Ir a Instalación](guia/instalacion.md) |
| 📖 Uso | Cómo usar y personalizar el chatbot | [Ir a Uso](guia/uso.md) |
| 💻 Comandos | Referencia de comandos y scripts | [Ir a Comandos](referencia/comandos.md) |
| ❓ FAQ | Preguntas frecuentes | [Ir a FAQ](referencia/faq.md) |

---

## Requisitos mínimos

- Node.js v18 o superior
- Clave de API de [OpenAI](https://platform.openai.com/)
- Navegador web moderno (Chrome, Firefox, Edge)
- Conexión a internet

---

## Estado del proyecto

| Componente | Estado |
|---|---|
| Backend Node.js | ✅ Estable |
| Integración OpenAI | ✅ Estable |
| Frontend web | ✅ Estable |
| Soporte multi-idioma | 🚧 En desarrollo |
| Historial persistente | 🔜 Planificado |

---

## ¿Para quién es este proyecto?

<details>
<summary>👥 Ver perfiles de usuario recomendados</summary>

Este chatbot está pensado para distintos perfiles, cada uno con un caso de uso diferente:

| Perfil | Caso de uso principal | Nivel técnico |
|---|---|---|
| Desarrollador web | Integrar el chatbot en una app existente | Medio-alto |
| Emprendedor / startup | Soporte automatizado para clientes | Bajo-medio |
| Estudiante de DAW/DAM | Proyecto final de ciclo | Medio |
| Administrador de sistemas | Automatizar consultas internas | Medio |

Si eres **estudiante**, empieza por el [Quickstart](guia/quickstart.md) y la [guía de instalación](guia/instalacion.md).

Si eres **desarrollador** buscando integrar el chatbot en un producto, consulta los [casos de uso reales](extra/casos-de-uso.md) y la [comparativa de modelos](extra/comparativa-modelos.md).

Si tienes dudas sobre terminología, el [glosario](extra/glosario.md) te será útil.

</details>

---

## Recursos externos

- [Documentación oficial de OpenAI](https://platform.openai.com/docs)
- [Node.js — sitio oficial](https://nodejs.org/)
- [Express.js — framework web](https://expressjs.com/)

---

> 💡 **Tip:** Si es tu primera vez, empieza por la [guía de Quickstart](guia/quickstart.md).
