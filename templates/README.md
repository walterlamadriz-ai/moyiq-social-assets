# Templates

`dark-quote.html` — plantilla oscura tipo "quote" (título + párrafo, sin cards de datos).
Usada por posts como netflix, paradoja, manifiesto.

Fix 24-sep-2026: el párrafo de cuerpo estaba en ~22px y el bloque quedaba
descentrado verticalmente (mucho espacio vacío arriba o abajo según el post).
Se subió el body a 30px y se ancló el bloque arriba (mismo criterio que las
plantillas claras con cards), dejando el logo fijo abajo.

Para generar un post nuevo: duplicar el HTML, cambiar eyebrow/título/párrafo/
acento, servir con `python3 -m http.server` y capturar con Playwright a
1080x1350 (ver ejemplo abajo). No usar Higgsfield para este tipo de post
estático de texto — reservar los créditos para lo que sí lo necesite.

```js
const { chromium } = require('playwright');
const browser = await chromium.launch();
const page = await browser.newPage({ viewport: { width: 1080, height: 1350 } });
await page.goto('http://localhost:PORT/mi-post.html');
await page.screenshot({ path: 'post-XX-nombre.jpg', type: 'jpeg', quality: 95 });
await browser.close();
```
