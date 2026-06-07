# ia_para_trampa
Chat Interactivo con OpenRouter  
Una aplicación web sencilla y moderna que permite conversar con modelos de lenguaje a través de la API de **OpenRouter**. Funciona completamente en el navegador, usando **Tailwind CSS** desde CDN y **streaming** para que las respuestas se muestren en tiempo real.

## 🌟 Características  
- **Diseño responsive** con Tailwind CSS.  
- **Streaming** de respuestas (texto que se escribe a medida que la API lo genera).  
- **Gestión de la API Key** mediante `localStorage`:  
  - Si no hay clave guardada, se muestra un prompt flotante al cargar la página.  
  - La clave se guarda y se reutiliza automáticamente en visitas posteriores.  
  - Botón de **Configuración** para cambiar o borrar la clave.  
- **Sin dependencias externas** (solo HTML, CSS y JavaScript).  
- **Listo para publicar** en **GitHub Pages** (cumple con la política de seguridad descrita).  

## 📦 Requisitos  
- Navegador moderno (Chrome, Firefox, Edge, Safari, etc.).  
- Una **API Key** válida de OpenRouter (obtenible en tu cuenta de OpenRouter).  

## 🚀 Instalación y uso rápido  
1. **Clona o descarga** este repositorio.  
   ```bash
   git clone https://github.com/tu-usuario/tu-repo-chat-openrouter.git
   cd tu-repo-chat-openrouter
   ```
2. **Abre** el archivo `index.html` en tu navegador (puedes arrastrarlo a una ventana o usar un servidor local si prefieres).  
3. **Primera visita**: si no tienes la API Key guardada, aparecerá un cuadro flotante solicitándote la clave.  
   - Ingresa tu API Key (ej. `sk-...`).  
   - Pulsa **Guardar**. La clave se almacenará en `localStorage` y no volverá a preguntar en futuros recargas.  
4. **Usa el chat**: escribe tu mensaje y pulsa **Enviar** (o la tecla `Enter`).  
   - Las respuestas se irán construyendo en tiempo real.  
5. **Configuración / Cerrar sesión**: haz clic en **Configuración** para:  
   - Cambiar la API Key.  
   - Borrar la clave (deja vacío el prompt).  

### Encriptar la API Key antes de guardarla  
Para mayor seguridad, puedes encriptar la clave antes de guardarla en `localStorage`. Usa la siguiente secuencia en la consola de la página (F12 → Console) y espera 2 segundos a que se cargue la librería:

```javascript
var script = document.createElement('script');
script.src = "https://cdnjs.cloudflare.com/ajax/libs/crypto-js/4.1.1/crypto-js.min.js";
document.head.appendChild(script);

// (Espera 2 segundos a que cargue y luego ejecuta la línea de abajo)
CryptoJS.AES.encrypt("tu-api-key-real-de-openrouter", "tu-contraseña-secreta").toString();
```

- Sustituye **`tu-api-key-real-de-openrouter`** por tu API Key de OpenRouter.  
- Sustituye **`tu-contraseña-secreta`** por una contraseña que solo tú conozcas.  
- Copia el resultado que devuelve `toString()` y pégalo en el campo de la ventana emergente cuando se te solicite la API Key.  

De esta forma la clave queda cifrada y solo podrás descifrarla dentro del propio script del chat, manteniéndola segura en `localStorage`.

## 📂 Estructura del proyecto  
```
. ├── index.html   # Archivo único que contiene todo el front‑end.
└── README.md      # Este documento.
```

## 🛠️ Personalización  
- **Cambiar el modelo**: modifica la constante `model` dentro de la función `streamOpenRouterResponse` (ej. `gpt-4`, `mistralai/Mistral-7B-Instruct-v0.2`).  
- **Estilos**: Tailwind CSS se carga desde CDN; puedes sobrescribir clases en la sección `<style>` del `<head>` si deseas ajustes visuales.  

## 📢 Publicar en GitHub Pages  
1. **Commit** y **push** los cambios a la rama `main` (o la rama que configures como fuente).  
2. En tu repositorio de GitHub, ve a **Settings → Pages** y selecciona la rama y la carpeta raíz (`/`).  
3. GitHub Pages construirá el sitio y te dará una URL pública (ej. `https://tu-usuario.github.io/tu-repo-chat-openrouter/`).  

> La política de GitHub Pages requiere que la API Key **no** se incluya en el código fuente. Este proyecto la guarda (y opcionalmente la encripta) en `localStorage`, por lo que es segura para publicación.
