# CONTEXT.md — Ivital

## 1. Qué es
Herbolario y espacio de salud integral en Las Palmas de Gran Canaria (C/ Francisco Rodríguez 42), de Dunia Moreno (@dunia_ms). Combina fitoterapia, nutrición, productos naturales y formación para acompañar la salud desde una visión integrativa.

## 2. Stack y entorno
**Lenguajes / formatos**
- HTML5 + CSS3 (variables CSS) + JavaScript vanilla, todo inline en cada archivo. No hay bundler ni build step.
- Markdown para documentación interna (CLAUDE.md, ideas).
- PNG/JPG para piezas gráficas y fotografía.

**Frameworks / dependencias externas**
- Google Fonts: Cormorant Garamond + Inter (cargadas vía CDN en `Landing/Landing Page.html`).
- Sin `package.json`, sin Node, sin Python, sin frameworks. Proyecto 100% estático.

**Rutas importantes (raíz del proyecto)**
- `CLAUDE.md` — directrices del proyecto (modelos, marca, estilo).
- `ideas para implementar en la web.md` — backlog de contenidos / servicios.
- `Landing/Landing Page.html` — landing principal en edición.
- `Landing/images/` — fotografía de producto, tienda, dunia.png.
- `Landing/images/brand/` — logos (`logo_ivital.png`, `_full`, `_white`, `_raw`).
- `Landing/reference/` — capturas de referencia visual.
- `Publicaciones/` — piezas Instagram ya publicadas (PNG).
- `Publicaciones_pendientes/fotos/` — slides en HTML listos para exportar a PNG.
- `Publicaciones_pendientes/reels/` — guiones y portadas de reels.
- `Fotos/` — fotografía original sin procesar (Ivital-XX.jpg).

**Puertos locales**
- No aplica. Abrir HTML directamente con doble click o con `python3 -m http.server 8000` para previsualizar.

**Variables de entorno**
- Ninguna. PENDIENTE: si se añade backend, formulario o analítica, documentar aquí los nombres (NO valores) de las claves.

**Hosting / dominio**
- Dominio: `ivital.es` (registrado).
- Hosting: Hostinger (contratado).
- Deploy intermedio recomendado: Netlify Drop para previews rápidos.

## 3. Estado actual
**Hecho**
- Landing v1 (`Landing/Landing Page.html`) maquetada con paleta navy/crema y secciones: hero, servicios, sobre Dunia, reseñas Google reales, productos, mapa, contacto, WhatsApp FAB, modal "Catálogo próximamente".
- Brand kit extraído: logos en variantes (color/blanco/full/raw).
- Reseñas reales de Google integradas.
- Paquete listo para deploy estático (`index.html` + `images/`) generado en sesión previa, exportado a `~/Downloads/ivital-web.zip` (2.2 MB).
- PDF de presentación generado (descartado por pérdida de calidad).
- Plantillas HTML para publicaciones de Instagram (fotos + reels) en `Publicaciones_pendientes/`.

**A medias**
- Deploy en producción: el zip está listo pero no se ha subido a Netlify ni a Hostinger todavía.
- Migración del título H1 a "Salud natural, desde la raíz" aplicada en la última versión, pendiente de re publicar.

**Siguiente**
- Subir el zip a Netlify Drop o a `public_html` en Hostinger.
- Conectar dominio `ivital.es` al hosting elegido y forzar HTTPS.
- Dar de alta el repositorio en GitHub (esta tarea).
- Alta y verificación de Google Business Profile + Google Search Console.
- Sustituir el modal "Catálogo próximamente" por un catálogo real.
- Páginas legales (Aviso legal, Privacidad, Cookies) RGPD compliant.
- Schema.org `LocalBusiness` + `Store` para SEO local.

## 4. Decisiones de arquitectura
- **HTML estático, sin framework.** Razón: la landing debe cargar instantánea, no requiere lógica de servidor, y Dunia debe poder editar el contenido sin pipeline de build. NO introducir React/Vue/Astro salvo que se justifique una sección dinámica real.
- **Todo el CSS y JS inline en el HTML.** Razón: simplicidad de despliegue (un solo archivo) y previsualización offline. NO trocear en archivos sueltos hasta que el peso de la landing lo exija.
- **Paleta corporativa fija: navy `#1a365d`, crema `#F5F0E8`/`#EDE8DD`, oro `#b8935a`.** Definida en `CLAUDE.md`. NO modificar tokens de color sin actualizar `CLAUDE.md`.
- **Tipografía: Cormorant Garamond (display) + Inter (cuerpo) en la landing; Georgia + system-ui en publicaciones.** NO mezclar familias nuevas.
- **Editorial / minimalista, mucho aire, emojis con moderación (🌿 ✨).** Estilo definido en `CLAUDE.md`.
- **Modelos por tarea:** Opus para planificación, Sonnet para desarrollo y contenido, Haiku para tareas ligeras (definido en `CLAUDE.md`).
- **Imágenes de pacientes / clientes / personas:** PENDIENTE: política formal de consentimiento. De momento solo se usan fotos del local, productos y de la propia Dunia (consentido).

## 5. Convenciones
- **Idioma de UI y contenido:** español (es ES). Tono cercano, profesional, integrativo.
- **Naming de archivos:** `kebab_case` o `snake_case` minúscula (`producto_01.jpg`, `logo_ivital_white.png`). Las publicaciones siguen el patrón `NN_tema_slideX.html` (ej. `02_mieles_yoge_slide1.html`).
- **Carpetas con espacios:** evitar. `Landing Page.html` es legacy y debería renombrarse a `landing.html` antes de mover a producción.
- **Branding:** logos en `Landing/images/brand/`; referencias visuales en `Landing/reference/` (no se sirven en la web final, sólo para inspiración).
- **Encoding:** UTF 8.
- **Indentación HTML/CSS:** 2 espacios.
- **Comentarios de edit mode:** los bloques `/*EDITMODE-BEGIN*/ ... /*EDITMODE-END*/` son zonas de configuración rápida. Respetar marcadores al editar.
- **Workflow de publicación:**
  1. Editar `Landing/Landing Page.html`.
  2. Probar abriendo en navegador.
  3. Copiar a `deploy/index.html` con la carpeta `images/` adjunta.
  4. Empaquetar en zip y subir a hosting.

## 6. Pendientes y bloqueos
- Subida del zip a Netlify o Hostinger. PENDIENTE: decisión final entre Netlify (rápido, dominio `*.netlify.app` inicial) vs Hostinger directo (`ivital.es`).
- Apuntar DNS de `ivital.es` al hosting elegido. PENDIENTE: A record / CNAME según destino.
- Certificado SSL. PENDIENTE: activación 1 click en hPanel o auto en Netlify.
- Catálogo real de productos. PENDIENTE: lista definitiva + fotografía pendiente de Dunia.
- Google Business Profile. PENDIENTE: verificación por postal o teléfono.
- Páginas legales RGPD. PENDIENTE: redacción Aviso legal, Política de privacidad, Cookies.
- Schema.org `LocalBusiness`. PENDIENTE: implementación en `<head>` con horarios, dirección y teléfono.
- Renombrar `Landing Page.html` a `landing.html` (espacio en nombre rompe rutas en hosting).
- Decisión sobre formulario de contacto: ¿usar solo WhatsApp/Instagram o añadir formulario con backend? PENDIENTE.

## 7. Comandos frecuentes
Proyecto estático sin build. Los comandos clave son:

```bash
# Previsualizar la landing en local (puerto 8000)
cd "Landing" && python3 -m http.server 8000
# luego abrir http://localhost:8000/Landing%20Page.html

# Validar HTML rápido
npx -y html-validate "Landing/Landing Page.html"

# Empaquetar para deploy (después de copiar a /deploy)
cd deploy && zip -rq ../ivital-web.zip .

# Deploy a Netlify Drop
# Abrir https://app.netlify.com/drop y arrastrar ivital-web.zip

# Deploy a Hostinger (vía hPanel)
# Subir ivital-web.zip a public_html y extraer ahí

# Git (tras inicializar)
git status
git add -A && git commit -m "feat: <descripcion>"
git push

# GitHub CLI
gh repo view --web         # abrir el repo en navegador
gh repo create Ivital --private --source=. --remote=origin --push
```

PENDIENTE: añadir comandos de optimización de imágenes (sharp/imagemin) cuando se automatice el pipeline de fotos.
