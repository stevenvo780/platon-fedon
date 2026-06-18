# Platón — Fedón (84c–102a)

Deck académico autocontenido en **reveal.js 5.1.0** (CDN), tema *night*, tipografía serif (EB Garamond), notas del ponente y soporte LaTeX vía MathJax 3.

**Tema:** Refutación de Simmias y Cebes · La Teoría de las Formas (Fedón 84c–102a) · 10 slides.

> Exposición dictada por Steven Vallejo, jue 11 jun 2026. Versión escindida de [`stevenvo780/expos-junio-2026`](https://github.com/stevenvo780/expos-junio-2026) como proyecto atómico: 1 deck = 1 repo.

## Preview local

Los decks usan plugins de reveal.js (notas, math) que requieren servirse por HTTP — **no** funcionan abriendo `file://` directamente.

```bash
cd platon-fedon
python3 -m http.server 8099
# luego, en el navegador:
#   http://localhost:8099/
```

### Atajos de teclado (reveal.js)

- **`S`** — abre la vista del ponente (*speaker notes*) con el guion hablado por slide + temporizador.
- **`F`** — pantalla completa · **`O`** / **`Esc`** — vista general · **`B`** — pantalla en negro.
- **`←` / `→` / `Espacio`** — navegar. Los bullets aparecen de a uno (fragments).
- **`?`** — ayuda con todos los atajos.

## Estructura

```
platon-fedon/
├── README.md
├── vercel.json          # cleanUrls + trailingSlash
└── index.html           # deck autocontenido (10 slides)
```

`index.html` es **self-contained**: solo depende de CDNs públicos (jsDelivr para reveal.js + MathJax, Google Fonts para EB Garamond). No hay build step ni `node_modules`.

## Deploy en Vercel

Sitio estático puro. Configuración:

- *Framework Preset* = **Other**
- *Build Command* = vacío
- *Output Directory* = `.`

Con la CLI:

```bash
vercel --prod
```

## Notas técnicas

- **reveal.js fijado** a `5.1.0` vía jsDelivr para reproducibilidad.
- **MathJax 3** vía plugin `RevealMath.MathJax3`. Los términos griegos (ἁρμονία, μέθεξις, ἀθάνατον…) van como texto Unicode (EB Garamond trae griego politónico); solo el esquema lógico del argumento final usa LaTeX (`\[ … \]`).
- **SRI omitido a propósito**: el plugin de math de reveal carga MathJax internamente sin punto donde fijar hash. Para endurecer en producción, vendorizar los assets en `vendor/` o fijar `integrity="sha384-…"` en los `<script>`/`<link>`.

## Créditos

- Autor: **Steven Vallejo** — <stevenvallejo780@gmail.com>
- Fuente: *Fedón* de Platón (texto griego estándar 84c–102a).
- Repo origen: [`stevenvo780/expos-junio-2026`](https://github.com/stevenvo780/expos-junio-2026)