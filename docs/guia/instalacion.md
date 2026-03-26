# 🔧 Instalación detallada

## Objetivo

Instalar y configurar todos los componentes del chatbot: Node.js, dependencias npm, variables de entorno y estructura del proyecto.

---

## Requisitos del sistema

| Componente | Versión mínima | Cómo verificar |
|---|---|---|
| Node.js | v18.0.0 | `node --version` |
| npm | v9.0.0 | `npm --version` |
| Git | v2.30+ | `git --version` |
| RAM disponible | 512 MB | — |

---

## Pasos

### 1. Instalar Node.js

Si aún no tienes Node.js instalado, descárgalo desde [nodejs.org](https://nodejs.org/) o usa un gestor de versiones:

```bash
# Con nvm (recomendado para gestionar múltiples versiones)
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
nvm install 18
nvm use 18
```

### 2. Clonar e instalar el proyecto

```bash
git clone https://github.com/tu-usuario/chatbot-ia.git
cd chatbot-ia
npm install
```

Las dependencias principales que se instalarán son:

- `express` — servidor HTTP
- `openai` — cliente oficial de OpenAI
- `dotenv` — gestión de variables de entorno
- `cors` — cabeceras CORS para el frontend

### 3. Configurar las variables de entorno

```bash
cp .env.example .env
nano .env   # o usa tu editor preferido
```

Contenido del `.env`:

```bash
# Clave de API de OpenAI (obligatorio)
OPENAI_API_KEY=sk-proj-xxxxxxxxxxxxxxxx

# Puerto del servidor
PORT=3000

# Modelo de IA a usar
OPENAI_MODEL=gpt-4o-mini

# Número máximo de tokens por respuesta
MAX_TOKENS=500
```

### 4. Verificar la estructura del proyecto

Una vez instalado, la estructura de carpetas debe ser:

```
chatbot-ia/
├── server.js          # Servidor principal
├── .env               # Variables de entorno (no subir a Git)
├── .env.example       # Plantilla de variables
├── package.json
└── public/
    ├── index.html     # Interfaz de usuario
    ├── style.css
    └── app.js
```

---

## Verificación

```bash
# Comprueba que Node.js está disponible
node --version   # Debe mostrar v18.x.x o superior

# Comprueba que las dependencias se instalaron
ls node_modules | head -5

# Arranca el servidor y comprueba que responde
npm start
curl http://localhost:3000/health
# Respuesta esperada: {"status":"ok"}
```

---

## Errores frecuentes

<details>
<summary>❌ <code>npm install</code> falla con errores de permisos</summary>

**Causa:** Problemas de permisos en el directorio global de npm.

**Solución:**

```bash
# Configura npm para no usar sudo
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.bashrc
source ~/.bashrc
```

</details>

<details>
<summary>❌ <code>Cannot find module 'openai'</code></summary>

**Causa:** Las dependencias no se instalaron correctamente.

**Solución:**

```bash
rm -rf node_modules package-lock.json
npm install
```

</details>

<details>
<summary>❌ El fichero <code>.env</code> no se carga</summary>

**Causa:** El fichero `.env` no está en la raíz del proyecto o tiene un error de formato.

**Solución:** Asegúrate de que la primera línea de `server.js` incluye:

```javascript
require('dotenv').config();
```

Y de que el fichero `.env` está en el mismo directorio que `server.js`.

</details>

---

> ➡️ Siguiente paso: [Guía de uso del chatbot](uso.md)
