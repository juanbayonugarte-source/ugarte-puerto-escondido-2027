# Familia Ugarte · Año Nuevo 2027 · Puerto Escondido

Presentación de viaje familiar (sitio estático de una sola página) para Año Nuevo
2026–27 en Puerto Escondido, Oaxaca. 25 personas, 7 noches, tres casas evaluadas.
Casa favorita destacada: **Escapadita 292**.

## Estructura

```
.
├── index.html        # Toda la presentación (CSS + JS inline)
├── images/           # Fotos de las 3 casas (AVIF, auto-hospedadas)
├── .nojekyll         # Evita el procesamiento Jekyll en GitHub Pages
├── netlify.toml      # Config de deploy para Netlify
└── vercel.json       # Config de deploy para Vercel
```

## Ver localmente

```bash
python3 -m http.server 8000
# abrir http://localhost:8000
```

## Deploy

**GitHub Pages** (activo): Settings → Pages → Branch `main` / root.

**Netlify** (alternativa, requiere login una vez):
```bash
npx netlify-cli deploy --prod --dir=.
```

**Vercel** (alternativa, requiere login una vez):
```bash
npx vercel --prod
```

## Notas de implementación

- Imágenes auto-hospedadas en formato **AVIF** (ya altamente comprimido) con
  fallback automático al CDN de escapadita.com.mx vía `onerror`.
- Imagen de la casa favorita precargada (`<link rel="preload">`) para mejorar el LCP.
- `loading="lazy"` + `decoding="async"` en las imágenes secundarias.
- Handlers de scroll combinados y limitados con `requestAnimationFrame`.
- Respeta `prefers-reduced-motion` (campo de estrellas estático si está activo).
- Cuenta regresiva en vivo hacia la medianoche del 31 Dic 2026.
- Metadatos Open Graph / Twitter para previews ricos al compartir por WhatsApp/iMessage.
