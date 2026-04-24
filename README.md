# 🤖 n8n — Automatización de Guiones e Ideas para Contenido

Flujo de automatización en n8n que monitorea cuentas de X/Twitter,
evalúa contenido con IA y genera ideas listas para producción en formato
Reel, Carrusel y Estática.

---

## ⚙️ ¿Qué hace este flujo?

1. **Disparo automático** cada 2 horas via Schedule Trigger
2. **Scrapeo de X/Twitter**: monitorea una lista configurable de cuentas
3. **Generación de keywords** con GPT-4o para búsqueda de contenido relevante
4. **Búsqueda cruzada** (palabras clave × usuarios) via Twitter API
5. **Score narrativo**: evalúa el potencial viral de cada tweet
6. **Generación de ideas** con GPT-4o + contexto estratégico desde Supabase (vector store)
7. **Output estructurado** en JSON con ideas para Reel, Carrusel y Estática
8. **Registro en Google Sheets** para revisión y aprobación humana

---

## 🛠 Tecnologías utilizadas

- [n8n](https://n8n.io/) — orquestación del flujo
- **OpenAI GPT-4o** — generación de ideas y scoring
- **Supabase** — vector store con contexto estratégico del cliente
- **Twitter/X API** — scraping y búsqueda de tweets
- **Google Sheets** — panel de aprobación humana
- **JavaScript** — nodos de transformación y lógica custom

---

## 📁 Estructura del output (por idea)

```json
{
  "id": "1",
  "idea": "Descripción general del contenido",
  "titulo": "Título del post o video",
  "texto_base": "Caption estilo tweet",
  "plataforma": "Instagram / X / YouTube",
  "reel": "Guion breve para video corto",
  "carrusel": "Estructura de slides",
  "estatica": "Frase para imagen o placa",
  "aprobado": false,
  "procesada": ""
}
```

---

## 🚀 Cómo importar el flujo

1. Abrí tu instancia de n8n
2. Andá a **Workflows → Import from file**
3. Seleccioná el archivo `.json` de este repo
4. Configurá tus credenciales:
   - OpenAI API Key
   - Twitter/X API Bearer Token
   - Supabase URL + API Key
   - Google Sheets OAuth2

---

## 📋 Requisitos

- n8n v1.0+
- Cuenta OpenAI con acceso a GPT-4o
- Twitter/X API (Basic tier o superior)
- Proyecto en Supabase con tabla vectorial configurada
- Google Sheets con columnas: `row_id`, `autor`, `idea`, `titulo`,
  `texto_base`, `plataforma`, `reel`, `carrusel`, `estatica`,
  `score_narrativo`, `tweet_original_link`, `procesada`

---

## ⚠️ Importante

Este flujo **no incluye credenciales**. Antes de ejecutarlo
necesitás configurar todas las conexiones desde
**Settings → Credentials** en n8n.
