# 🚀 Quickstart — Chatbot con IA

## Objetivo

Poner en marcha el chatbot en menos de **5 minutos** siguiendo tres pasos simples: clonar, configurar y arrancar.

---

## Requisitos previos

- [x] Node.js v18+ instalado (`node --version`)
- [x] Cuenta en [OpenAI](https://platform.openai.com/) con créditos disponibles
- [x] Git instalado en el sistema
- [x] Terminal / línea de comandos disponible

---

## Pasos

### Paso 1 — Clonar el repositorio

```bash
git clone https://github.com/tu-usuario/chatbot-ia.git
cd chatbot-ia
```

### Paso 2 — Instalar dependencias y configurar variables de entorno

```bash
npm install
cp .env.example .env
```

Edita el fichero `.env` y añade tu clave de API:

```bash
OPENAI_API_KEY=sk-proj-xxxxxxxxxxxxxxxxxxxxxxxx
PORT=3000
```

### Paso 3 — Arrancar el servidor

```bash
npm start
```

Abre tu navegador en [http://localhost:3000](http://localhost:3000) y el chatbot estará listo.

---

## Verificación

Una vez arrancado, deberías ver en la terminal:

```
✅ Servidor escuchando en http://localhost:3000
✅ Conectado a OpenAI API
```

Y en el navegador, una interfaz de chat como esta:

![Interfaz del chatbot en el navegador](../assets/captura-chat.png)

Escribe un mensaje de prueba, por ejemplo `Hola, ¿qué puedes hacer?`, y comprueba que recibes respuesta en menos de 3 segundos.

---

## Errores frecuentes

<details>
<summary>❌ Error: <code>Invalid API Key</code></summary>

**Causa:** La clave de OpenAI no es válida o no se ha añadido correctamente al fichero `.env`.

**Solución:**
1. Accede a [platform.openai.com/api-keys](https://platform.openai.com/api-keys)
2. Genera una nueva clave
3. Pégala en `.env` sin espacios ni comillas adicionales

```bash
# Correcto
OPENAI_API_KEY=sk-proj-abc123...

# Incorrecto
OPENAI_API_KEY="sk-proj-abc123..."  # No uses comillas
OPENAI_API_KEY= sk-proj-abc123...  # No dejes espacio tras =
```

</details>

<details>
<summary>❌ Error: <code>EADDRINUSE: address already in use :::3000</code></summary>

**Causa:** El puerto 3000 ya está ocupado por otro proceso.

**Solución:**

```bash
# En Linux/Mac — mata el proceso en el puerto 3000
kill -9 $(lsof -ti:3000)

# O cambia el puerto en .env
PORT=3001
```

</details>

---

> ➡️ Siguiente paso: [Guía de instalación detallada](instalacion.md)
