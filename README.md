# Soltá — App de PNL

**"Soltá lo que te pesa."**  
Cambio de submodalidades guiado en 5 minutos.

🌐 **App en vivo:** https://solta.vercel.app

---

## Qué es

App mobile-first PWA instalable. Guía al usuario por el protocolo clásico de cambio de submodalidades de PNL:

1. Intensidad inicial (0-10)
2. Categoría de lo que pesa
3. Formato de representación (imagen / película / sonido / metáfora)
4. Disociación (pantalla de cine)
5. Mapeo Visual — sliders de brillo, distancia, tamaño + opciones avanzadas
6. Mapeo Auditivo — volumen, distancia
7. Mapeo Kinestésico — peso, intensidad, temperatura
8. Transformación — sugerencias dinámicas según lo que registró el usuario
9. Re-integración post-disociación
10. Cierre con respiración, anclaje y medición del cambio

---

## Stack

- Vanilla JS (sin framework)
- Tailwind CSS por CDN
- Web Audio API — música ambient 432Hz generada en tiempo real
- PWA — service worker `solta-v4`, instalable en home screen
- Sin backend — todo en `localStorage`
- Deploy: Vercel (estático)

---

## Estructura

```
solta/
├── index.html              ← App completa (~93KB)
├── sw.js                   ← Service worker (solta-v4)
├── manifest.json           ← PWA manifest
├── vercel.json             ← Headers de seguridad + outputDirectory
├── package.json            ← Metadata
├── icon-192.png
├── icon-512.png
├── icon-maskable-512.png
├── apple-touch-icon.png
├── favicon-32.png
├── PASO_A_PASO.md          ← Guía de deploy y actualizaciones
└── README.md               ← Este archivo
```

---

## Actualizar

Ver `PASO_A_PASO.md` para el flujo completo.

Resumen: editás → commit → push → Vercel redeploya en 30 segundos.

---

## Datos de contacto embebidos

- WhatsApp: `wa.me/5491170599871`
- Instagram: `@jeremiasvargascoach`
- Web: `jeremiasvargascoach.com`

Para cambiarlos: `index.html` líneas ~418-421.
