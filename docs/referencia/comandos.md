# 💻 Referencia de Comandos

## Objetivo

Consultar rápidamente todos los scripts npm, comandos Git y llamadas a la API disponibles en el proyecto.

---

## Requisitos

- Proyecto instalado ([ver Instalación](../guia/instalacion.md))
- Terminal abierta en la raíz del proyecto

---

## Pasos

### Ejecutar los scripts del proyecto

Todos los scripts se lanzan desde la raíz del proyecto con `npm run <script>`.

---

## Scripts npm disponibles

| Comando | Para qué sirve | Cuándo usarlo |
|---|---|---|
| `npm start` | Arranca el servidor en producción | Uso normal |
| `npm run dev` | Arranca con recarga automática (nodemon) | Desarrollo |
| `npm test` | Ejecuta los tests unitarios | Antes de hacer commit |
| `npm run lint` | Comprueba el estilo del código | Desarrollo |
| `npm run build` | Genera los estáticos optimizados | Antes de desplegar |

```bash
# Desarrollo con recarga automática
npm run dev

# Producción
npm start

# Tests
npm test
```

---

## Comandos Git del flujo de trabajo

```bash
# 1. Crear una rama de feature
git checkout -b feature/nueva-funcionalidad

# 2. Añadir cambios y hacer commit
git add .
git commit -m "feat: add conversation history support"

# 3. Subir la rama al remoto
git push -u origin feature/nueva-funcionalidad

# 4. Fusionar a main (opción local)
git checkout main
git merge feature/nueva-funcionalidad
git push
```

---

## Llamadas a la API con curl

| Método | Endpoint | Descripción |
|---|---|---|
| `GET` | `/health` | Comprueba si el servidor está activo |
| `POST` | `/api/chat` | Envía mensaje al chatbot |
| `DELETE` | `/api/chat/history` | Limpia el historial |

```bash
# Comprobar estado del servidor
curl http://localhost:3000/health

# Enviar mensaje al chatbot
curl -X POST http://localhost:3000/api/chat \
  -H "Content-Type: application/json" \
  -d '{"message": "Hola", "history": []}'

# Borrar historial de conversación
curl -X DELETE http://localhost:3000/api/chat/history
```

---

## Variables de entorno

| Variable | Descripción | Valor por defecto |
|---|---|---|
| `OPENAI_API_KEY` | Clave de API de OpenAI | *(obligatorio)* |
| `PORT` | Puerto del servidor | `3000` |
| `OPENAI_MODEL` | Modelo de IA a usar | `gpt-4o-mini` |
| `MAX_TOKENS` | Tokens máximos por respuesta | `500` |
| `NODE_ENV` | Entorno de ejecución | `development` |

---

## Verificación

```bash
# Comprueba que el servidor responde en todos los endpoints
curl http://localhost:3000/health
# ► {"status":"ok","uptime":42}

curl -X POST http://localhost:3000/api/chat \
  -H "Content-Type: application/json" \
  -d '{"message":"test","history":[]}'
# ► {"reply":"...","tokens_used":15}
```

---

## Errores frecuentes

<details>
<summary>❌ <code>npm run dev</code> da error: <code>nodemon: command not found</code></summary>

**Causa:** `nodemon` no está instalado globalmente.

**Solución:**

```bash
npm install -g nodemon
# o instalarlo solo en el proyecto
npm install --save-dev nodemon
```

</details>

<details>
<summary>❌ <code>curl</code> devuelve <code>Connection refused</code></summary>

**Causa:** El servidor no está arrancado o está en un puerto diferente.

**Solución:**

```bash
# Comprueba si el servidor está corriendo
ps aux | grep node

# Comprueba el puerto configurado en .env
cat .env | grep PORT
```

</details>

---

> 🔗 ¿Tienes dudas? Consulta la [FAQ](faq.md) o la [guía de uso](../guia/uso.md).
