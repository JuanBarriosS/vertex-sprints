# Tarjeta 6 — Optimizar imágenes y recursos estáticos

> **Descripción:** Reducir el peso de imágenes y archivos estáticos para mejorar la velocidad de carga sin deteriorar perceptiblemente la calidad visual.

---

### 1. Inventario de imágenes utilizadas / Peso actual

| Archivo | Peso |
| :--- | :--- |
| `vertex-wallpaper-dark.png` | 4821 KB |
| `vertex-wallpaper-light.png` | 4870 KB |
| `vertex-wallpaper-light-4k-v2.png` | 4870 KB |
| `showcase-careers-team.jpg` | 2492 KB |
| `whoweare-hero-visual.jpg` | 2473 KB |
| `services/digital-marketing-communications.jpg` | 2439 KB |
| `services/public-sector-large-projects.jpg` | 2262 KB |
| `services/innovation-digital-transformation.jpg` | 2258 KB |
| `services/software-development.jpg` | 2240 KB |
| `showcase-careers-design.jpg` | 2196 KB |
| `services/audiovisual-production.jpg` | 2074 KB |
| `services/strategic-design-branding.jpg` | 1969 KB |
| `services/trade-show-experiences.jpg` | 1933 KB |
| `team/sebastian-fuentes.png` | 1696 KB |
| `vertex-regional-map-coverage.png` | 1628 KB |
| `vertexPrincipal.png` | 1584 KB |
| `vertex-wallpaper-2.png` | 1379 KB |
| `projects/vertex-sprint.jpg` | 1258 KB |
| `vertex-wallpaper-1.png` | 1254 KB |
| `vertex-service-hero-background-v2.png` | 1215 KB |
| `projects/vertex-nexo.jpg` | 1050 KB |
| `projects/suite-de-vertex.jpg` | 909 KB |
| `projects/vertex-crm-pro.jpg` | 907 KB |
| `team/maria-gutierrez.png` | 857 KB |
| `capabilities-ecosystem.jpg` | 787 KB |
| `showcase-home-latam.jpg` | 650 KB |
| `showcase-home-design.jpg` | 622 KB |
| `showcase-careers-dev.jpg` | 604 KB |
| `talent-culture.jpg` | 602 KB |
| `showcase-home-dashboard.jpg` | 553 KB |
| `about-vision.jpg` | 548 KB |
| `team/juan-barrios.jpg` | 269 KB |
| `showcase-home-abstract.jpg` | 211 KB |
| `vertex-symbol.png` | 132 KB |
| `logo.png` | 119 KB |
| `team/juan-bejarano.jpg` | 118 KB |
| `vertex-logo.png` | 65 KB |
| `projects-hero-wallpaper.jpg` | 63 KB |
| `team/paula-mendoza.jpg` | 60 KB |
| `team/ray-mendoza.jpg` | 15 KB |
| `demo-latam-network.svg`, `demo-ai-operations.svg`, `demo-software-platform.svg`, `demo-brand-system.svg` | 1 KB c/u |

> **Conclusión:** El repositorio tiene 44 archivos en `public/images` (más `favicon.ico`, `favicon.png` y 4 SVG genéricos de Next.js en `public/`, ajenos al contenido del sitio). El peso total de `public/images` es de 55 MB.

### 2. Archivos duplicados o sin uso

| Archivo | Hallazgo |
| :--- | :--- |
| `vertex-wallpaper-light.png` | Contenido idéntico (mismo hash MD5) a `vertex-wallpaper-light-4k-v2.png`, y ninguno de los dos tiene referencia en el código del repo. |
| `vertex-wallpaper-light-4k-v2.png` | Duplicado exacto del anterior, sin referencia en el código. |

> **Conclusión:** Estos dos archivos (9.6 MB) están en el repo sin usarse en ninguna página. El resto de las imágenes sí tiene referencia activa en el código, algunas de forma dinámica (ej. las de `services/` se arman con `${service.id}`).

### 3. Dimensiones apropiadas para cada uso

- **Componente:** `src/components/pages/TeamPageContent.tsx`
- **Hallazgo:** las fotos de equipo se renderizan con `fill` y sin la prop `sizes`, dentro de un contenedor de 128x128px. Sin `sizes`, Next.js asume por defecto que la imagen puede ocupar el 100% del viewport y genera/sirve una versión más grande de lo que realmente se muestra.

> **Conclusión:** Es el único punto donde el tamaño servido no está acotado al tamaño real de visualización. El resto de los componentes con `fill` (proyectos, servicios, mapa regional, ecosistema de capacidades) ya declaran `sizes` correctamente, y los logos/íconos usan `width/height` fijos acordes a su tamaño real.

### 4. Carga diferida (lazy loading)

- **Alcance revisado:** todos los usos de imagen en `src/components` y `src/app`.

> **Conclusión:** No hay ningún `<img>` nativo en el proyecto; todas las imágenes pasan por `next/image`, que aplica lazy loading por defecto. No se encontró ningún `unoptimized` ni `loading="eager"` forzado, fuera de los casos donde sí corresponde carga inmediata (logo del header y símbolo de la página 404, marcados con `priority`).

### 5. Imágenes más grandes que su tamaño de visualización

| Archivo / Grupo | Hallazgo |
| :--- | :--- |
| `vertex-wallpaper-dark.png` (4821 KB, 3840x2160) | Se usa como `background-image` en CSS (no pasa por `next/image`), en formato PNG para contenido tipo gráfico/foto — un formato con compresión con pérdida (WebP/JPEG optimizado) pesaría una fracción de esto sin diferencia visible. |
| las 7 imágenes de `services/*.jpg` (2–2.4 MB c/u) | Mismo caso, JPG sin comprimir/optimizar a un peso razonable para web. |
| `team/sebastian-fuentes.png` y `team/maria-gutierrez.png` (1.7 MB y 857 KB) | Fotos de persona guardadas en PNG (sin necesidad real de transparencia útil salvo el canal alfa), mucho más pesadas de lo que darían en WebP. |

> **Conclusión:** El repo no tiene ningún paso de compresión de imágenes aplicado (ni build-time ni manual): los archivos están tal como se subieron originalmente. La carpeta `public/images` pesa 55 MB; convertir estos archivos a WebP los reduciría en el orden de 85-98% sin pérdida visible, según las pruebas hechas sobre copias locales.

### 6. Pérdida de calidad visible

> **Conclusión:** Sobre el estado actual del repo no aplica (no se ha tocado ningún archivo). En pruebas hechas sobre copias locales de `vertex-wallpaper-dark.png` y `team/sebastian-fuentes.png`, comprimir a WebP no mostró pérdida de calidad perceptible incluso con reducciones de 96-98% en peso — sirve como referencia de que la compresión es viable sin sacrificar apariencia.

### 7. Documentar los resultados

> **Conclusión:** Estado actual del repositorio: 55 MB en `public/images`, 2 archivos duplicados sin uso (9.6 MB), 1 componente (`TeamPageContent.tsx`) sin `sizes` en imágenes con `fill`, y ningún archivo pasado por un proceso de compresión. Pendiente de aplicar directamente sobre el repositorio de Vertex (no tengo permisos de escritura sobre ese GitHub).
