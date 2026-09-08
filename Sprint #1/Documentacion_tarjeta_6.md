Tarjeta 6 — Optimizar imágenes y recursos estáticos

Descripción: Reducir el peso de imágenes y archivos estáticos para mejorar la velocidad de carga sin deteriorar perceptiblemente la calidad visual.

1) Inventario de imágenes utilizadas / 3) Peso actual de las imágenes

* **Archivo:** vertex-wallpaper-dark.png ==> **Peso:** 4821 KB
* **Archivo:** vertex-wallpaper-light.png ==> **Peso:** 4870 KB
* **Archivo:** vertex-wallpaper-light-4k-v2.png ==> **Peso:** 4870 KB
* **Archivo:** showcase-careers-team.jpg ==> **Peso:** 2492 KB
* **Archivo:** whoweare-hero-visual.jpg ==> **Peso:** 2473 KB
* **Archivo:** services/digital-marketing-communications.jpg ==> **Peso:** 2439 KB
* **Archivo:** services/public-sector-large-projects.jpg ==> **Peso:** 2262 KB
* **Archivo:** services/innovation-digital-transformation.jpg ==> **Peso:** 2258 KB
* **Archivo:** services/software-development.jpg ==> **Peso:** 2240 KB
* **Archivo:** showcase-careers-design.jpg ==> **Peso:** 2196 KB
* **Archivo:** services/audiovisual-production.jpg ==> **Peso:** 2074 KB
* **Archivo:** services/strategic-design-branding.jpg ==> **Peso:** 1969 KB
* **Archivo:** services/trade-show-experiences.jpg ==> **Peso:** 1933 KB
* **Archivo:** team/sebastian-fuentes.png ==> **Peso:** 1696 KB
* **Archivo:** vertex-regional-map-coverage.png ==> **Peso:** 1628 KB
* **Archivo:** vertexPrincipal.png ==> **Peso:** 1584 KB
* **Archivo:** vertex-wallpaper-2.png ==> **Peso:** 1379 KB
* **Archivo:** projects/vertex-sprint.jpg ==> **Peso:** 1258 KB
* **Archivo:** vertex-wallpaper-1.png ==> **Peso:** 1254 KB
* **Archivo:** vertex-service-hero-background-v2.png ==> **Peso:** 1215 KB
* **Archivo:** projects/vertex-nexo.jpg ==> **Peso:** 1050 KB
* **Archivo:** projects/suite-de-vertex.jpg ==> **Peso:** 909 KB
* **Archivo:** projects/vertex-crm-pro.jpg ==> **Peso:** 907 KB
* **Archivo:** team/maria-gutierrez.png ==> **Peso:** 857 KB
* **Archivo:** capabilities-ecosystem.jpg ==> **Peso:** 787 KB
* **Archivo:** showcase-home-latam.jpg ==> **Peso:** 650 KB
* **Archivo:** showcase-home-design.jpg ==> **Peso:** 622 KB
* **Archivo:** showcase-careers-dev.jpg ==> **Peso:** 604 KB
* **Archivo:** talent-culture.jpg ==> **Peso:** 602 KB
* **Archivo:** showcase-home-dashboard.jpg ==> **Peso:** 553 KB
* **Archivo:** about-vision.jpg ==> **Peso:** 548 KB
* **Archivo:** team/juan-barrios.jpg ==> **Peso:** 269 KB
* **Archivo:** showcase-home-abstract.jpg ==> **Peso:** 211 KB
* **Archivo:** vertex-symbol.png ==> **Peso:** 132 KB
* **Archivo:** logo.png ==> **Peso:** 119 KB
* **Archivo:** team/juan-bejarano.jpg ==> **Peso:** 118 KB
* **Archivo:** vertex-logo.png ==> **Peso:** 65 KB
* **Archivo:** projects-hero-wallpaper.jpg ==> **Peso:** 63 KB
* **Archivo:** team/paula-mendoza.jpg ==> **Peso:** 60 KB
* **Archivo:** team/ray-mendoza.jpg ==> **Peso:** 15 KB
* **Archivos:** demo-latam-network.svg, demo-ai-operations.svg, demo-software-platform.svg, demo-brand-system.svg ==> **Peso:** 1 KB c/u

**Conclusión de la revisión:**
El repositorio tiene 44 archivos en public/images (más favicon.ico, favicon.png y 4 SVG genéricos de Next.js en public/, ajenos al contenido del sitio). El peso total de public/images es de 55 MB.

2) Archivos duplicados o sin uso

* **Archivo:** vertex-wallpaper-light.png ==> **Hallazgo:** contenido idéntico (mismo hash MD5) a vertex-wallpaper-light-4k-v2.png, y ninguno de los dos tiene referencia en el código del repo.
* **Archivo:** vertex-wallpaper-light-4k-v2.png ==> **Hallazgo:** duplicado exacto del anterior, sin referencia en el código.

**Conclusión de la revisión:**
Estos dos archivos (9.6 MB) están en el repo sin usarse en ninguna página. El resto de las imágenes sí tiene referencia activa en el código, algunas de forma dinámica (ej. las de services/ se arman con `${service.id}`).

4) Dimensiones apropiadas para cada uso

* **Componente:** src/components/pages/TeamPageContent.tsx ==> **Hallazgo:** las fotos de equipo se renderizan con `fill` y sin la prop `sizes`, dentro de un contenedor de 128x128px. Sin `sizes`, Next.js asume por defecto que la imagen puede ocupar el 100% del viewport y genera/sirve una versión más grande de lo que realmente se muestra.

**Conclusión de la revisión:**
Es el único punto donde el tamaño servido no está acotado al tamaño real de visualización. El resto de los componentes con `fill` (proyectos, servicios, mapa regional, ecosistema de capacidades) ya declaran `sizes` correctamente, y los logos/íconos usan `width`/`height` fijos acordes a su tamaño real.

5) Carga diferida (lazy loading)

* **Alcance revisado:** todos los usos de imagen en src/components y src/app.

**Conclusión de la revisión:**
No hay ningún `<img>` nativo en el proyecto; todas las imágenes pasan por `next/image`, que aplica lazy loading por defecto. No se encontró ningún `unoptimized` ni `loading="eager"` forzado, fuera de los casos donde sí corresponde carga inmediata (logo del header y símbolo de la página 404, marcados con `priority`).

6) Imágenes más grandes que su tamaño de visualización

* **Archivo:** vertex-wallpaper-dark.png (4821 KB, 3840x2160) ==> **Hallazgo:** se usa como `background-image` en CSS (no pasa por next/image), en formato PNG para contenido tipo gráfico/foto — un formato con compresión con pérdida (WebP/JPEG optimizado) pesaría una fracción de esto sin diferencia visible.
* **Archivo:** las 7 imágenes de services/*.jpg (2–2.4 MB c/u) ==> **Hallazgo:** mismo caso, JPG sin comprimir/optimizar a un peso razonable para web.
* **Archivo:** team/sebastian-fuentes.png y team/maria-gutierrez.png (1.7 MB y 857 KB) ==> **Hallazgo:** fotos de persona guardadas en PNG (sin necesidad real de transparencia útil salvo el canal alfa), mucho más pesadas de lo que darían en WebP.

**Conclusión de la revisión:**
El repo no tiene ningún paso de compresión de imágenes aplicado (ni build-time ni manual): los archivos están tal como se subieron originalmente. La carpeta public/images pesa 55 MB; convertir estos archivos a WebP los reduciría en el orden de 85-98% sin pérdida visible, según las pruebas hechas sobre copias locales.

7) Pérdida de calidad visible

**Conclusión de la revisión:**
Sobre el estado actual del repo no aplica (no se ha tocado ningún archivo). En pruebas hechas sobre copias locales de vertex-wallpaper-dark.png y team/sebastian-fuentes.png, comprimir a WebP no mostró pérdida de calidad perceptible incluso con reducciones de 96-98% en peso — sirve como referencia de que la compresión es viable sin sacrificar apariencia.

8) Documentar los resultados

**Conclusión de la revisión:**
Estado actual del repositorio: 55 MB en public/images, 2 archivos duplicados sin uso (9.6 MB), 1 componente (TeamPageContent.tsx) sin `sizes` en imágenes con `fill`, y ningún archivo pasado por un proceso de compresión. Pendiente de aplicar directamente sobre el repositorio de Vertex (no tengo permisos de escritura sobre ese GitHub).
