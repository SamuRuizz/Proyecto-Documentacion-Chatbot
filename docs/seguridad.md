# 🔒 Seguridad y Buenas Prácticas

## Objetivo

Identificar los principales riesgos de seguridad del chatbot y aplicar las medidas necesarias para proteger la clave de API, los datos de los usuarios y el servidor.

---

## ¿Por qué es importante la seguridad?

Un chatbot conectado a una API externa como OpenAI maneja información sensible: la clave de API (que tiene coste económico si se abusa de ella), los mensajes de los usuarios y la configuración del sistema. Un error de seguridad puede suponer desde una factura inesperada hasta una filtración de datos.

---

## Protección de la clave de API

La clave de OpenAI es el activo más crítico del proyecto. Si alguien la obtiene, puede generar peticiones a tu costa.

**Reglas básicas:**

- Guarda la clave **siempre** en el fichero `.env`, nunca en el código fuente
- Añade `.env` al fichero `.gitignore` antes del primer commit

```bash
# .gitignore — añade esta línea si no está
.env
```

- Establece un **límite de gasto mensual** en el panel de OpenAI para evitar sorpresas en la factura
- **Rota la clave** periódicamente desde [platform.openai.com/api-keys](https://platform.openai.com/api-keys)
- Si sospechas que la clave se ha filtrado, **revócala inmediatamente** y genera una nueva

---

## Validación de entradas del usuario

Nunca confíes en los datos que envía el usuario. Valida y limpia siempre el input antes de pasarlo a la API:

```javascript
// En server.js — validación básica del mensaje entrante
app.post('/api/chat', (req, res) => {
  const { message, history } = req.body;

  // Comprueba que el mensaje existe y no está vacío
  if (!message || typeof message !== 'string') {
    return res.status(400).json({ error: 'Mensaje inválido' });
  }

  // Limita la longitud del mensaje para evitar abusos
  if (message.length > 1000) {
    return res.status(400).json({ error: 'Mensaje demasiado largo' });
  }

  // Continúa con la lógica normal...
});
```

---

## Limitación de peticiones (Rate Limiting)

Sin límite de peticiones, un único usuario podría hacer miles de llamadas en segundos y agotar tu crédito de API. Instala `express-rate-limit`:

```bash
npm install express-rate-limit
```

```javascript
const rateLimit = require('express-rate-limit');

const limiter = rateLimit({
  windowMs: 60 * 1000,  // ventana de 1 minuto
  max: 20,              // máximo 20 peticiones por IP por minuto
  message: { error: 'Demasiadas peticiones, espera un momento.' }
});

app.use('/api/', limiter);
```

---

## Cabeceras de seguridad HTTP

Añade cabeceras de seguridad estándar con el paquete `helmet`:

```bash
npm install helmet
```

```javascript
const helmet = require('helmet');
app.use(helmet());
```

Esto protege contra ataques comunes como XSS, clickjacking y sniffing de contenido.

---

## Tabla resumen de medidas

| Medida | Prioridad | Dificultad | Paquete necesario |
|---|---|---|---|
| `.env` en `.gitignore` | 🔴 Crítica | Muy baja | — |
| Límite de gasto en OpenAI | 🔴 Crítica | Muy baja | — |
| Validación de inputs | 🟠 Alta | Baja | — |
| Rate limiting | 🟠 Alta | Baja | `express-rate-limit` |
| Cabeceras HTTP seguras | 🟡 Media | Muy baja | `helmet` |
| Autenticación de usuarios | 🟡 Media | Alta | `jsonwebtoken` |

---

## Buenas prácticas de desarrollo

Además de la seguridad técnica, hay hábitos de desarrollo que reducen el riesgo de errores:

- Haz **commits pequeños y frecuentes** con mensajes descriptivos
- Usa **ramas de feature** en Git y nunca trabajes directamente en `main`
- Revisa el código antes de fusionar (Pull Request, aunque trabajes solo)
- Mantén las dependencias actualizadas con `npm audit` regularmente

```bash
# Comprueba vulnerabilidades conocidas en las dependencias
npm audit

# Corrígelas automáticamente cuando sea posible
npm audit fix
```

---

> 🔗 [Volver al inicio](index.md) | 🏁 [Ver conclusiones](conclusiones.md)
