# Brillita — Registro Diario de Horas

PWA personal para registrar horas trabajadas por día y calcular automáticamente el total ganado (horas × valor por hora). Pensada para instalarse en la pantalla de inicio del iPhone y usarse sin conexión.

## Funcionalidad

- **Registrar**: agrega horas trabajadas y valor por hora de cualquier fecha; muestra el total en vivo antes de guardar. El resumen del día se calcula con tus registros reales (no datos de ejemplo).
- **Semanal**: horas y ganancias de la semana actual, gráfico de barras por día, historial completo con opción de borrar registros individuales o todos.
- **Perfil**: nombre, valor por hora predeterminado (se precarga en el formulario), meta diaria en dólares, totales históricos, y exportación a CSV.
- Todo se guarda con `localStorage` — **los datos quedan solo en tu dispositivo**, no hay backend ni servidor.
- Funciona offline gracias a un Service Worker que cachea la app.

## Publicar en GitHub Pages

1. Crea un repositorio nuevo en GitHub (por ejemplo `brillita`) y sube **todo el contenido de esta carpeta** a la raíz del repo (o a `/docs` si prefieres esa carpeta).
2. En GitHub: `Settings` → `Pages` → en "Build and deployment" elige `Deploy from a branch`, selecciona la rama `main` y la carpeta (`/root` o `/docs`).
3. Espera 1–2 minutos y tu app quedará disponible en:
   `https://tonyramon97.github.io/brillita/`
   (ajusta el nombre según el repo que crees).

> Importante: la PWA debe servirse por **HTTPS** (GitHub Pages ya lo hace) para que el Service Worker y el "Agregar a inicio" funcionen correctamente en iPhone.

## Instalar en iPhone (pantalla de inicio)

1. Abre el link de tu GitHub Pages en **Safari** (no funciona el "Agregar a inicio" desde Chrome en iOS).
2. Toca el ícono de **Compartir** (el cuadrado con la flecha hacia arriba).
3. Baja y toca **"Agregar a pantalla de inicio"**.
4. Confirma el nombre ("Brillita") y toca **Agregar**.
5. El ícono aparecerá en tu pantalla de inicio y se abrirá en modo standalone (sin barra de Safari), igual que una app nativa.

## Estructura del proyecto

```
brillita-pwa/
├── index.html          # App completa (UI + lógica)
├── manifest.json        # Configuración PWA (nombre, íconos, colores)
├── sw.js                 # Service worker (offline)
├── icons/
│   ├── icon-192.png
│   ├── icon-512.png
│   ├── icon-maskable-512.png
│   ├── apple-touch-icon.png
│   └── favicon-32.png
└── README.md
```

## Notas técnicas

- Sin build ni dependencias: HTML + Tailwind (CDN) + JS vanilla.
- Paleta de colores idéntica a tu diseño original (`primary #00666d`, `secondary #9b4500`, `secondary-container #fc8a40`, etc.), tipografía Inter y Material Symbols.
- Si quieres reiniciar todos los datos, usa el botón "Borrar todo" en la pestaña Semanal.
