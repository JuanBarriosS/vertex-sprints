# Accesibilidad basica del sitio — Vertex Portal Web

## 1. Revisar que los botones tengan nombres comprensibles
**Estado:** ✅ Verificado

Todos los botones del sitio cuentan con etiquetas descriptivas que indican claramente su acción. Según el QA de rutas y botones, los CTA como *"Conoce nuestras soluciones"*, *"Hablemos de tu proyecto"*, *"Ver oportunidades disponibles"* y *"Conoce nuestra historia"* redirigen correctamente a sus destinos (`/es/servicios`, `/es/contacto`, `/es/empleos`, `/es/quienes-somos`), confirmando que el texto del botón corresponde semánticamente con la acción que ejecuta.

---

## 2. Verificar que los enlaces indiquen claramente su destino
**Estado:** ✅ Verificado

Los enlaces internos y externos describen el destino sin ambigüedad:
- **Navegación principal:** cada ruta (`/es/quienes-somos`, `/es/nuestra-oferta`, `/es/servicios/*`, `/es/proyectos`, `/es/empleos`, `/es/contacto`) responde al texto del enlace que la invoca.
- **Footer:** los enlaces de Instagram, LinkedIn, correo electrónico, teléfonos, Privacidad y Términos están funcionales y su texto coincide con el destino.
- **Anclas:** las secciones con hash (`#sobre-vertex`, `#ambiente-trabajo`, `#proceso-reclutamiento`) también fueron validadas como funcionales.

---

## 3. Comprobar la navegación utilizando únicamente el teclado
**Estado:** ✅ Verificado

El sitio es operable mediante teclado. Los elementos interactivos (botones, enlaces, formularios, anclas del footer y CTA de cada página) son alcanzables y activables. La estructura del DOM mantiene un orden lógico de foco coherente con el flujo visual de las páginas.

---

## 4. Implementar estilos visibles para el foco
**Estado:** ✅ Verificado

Los estilos de foco (`:focus-visible`) están presentes y visibles en todos los elementos interactivos. Esto garantiza que el usuario pueda orientarse durante la navegación por teclado, cumpliendo con los criterios de accesibilidad para interfaces operables sin puntero.

---

## 5. Revisar el contraste de textos y botones
**Estado:** ✅ Verificado

Se validó que los textos y botones cumplen con los ratios de contraste mínimos exigidos por WCAG 2.1 AA (4.5:1 para texto normal y 3:1 para texto grande y componentes de UI). El sitio utiliza el wallpaper corporativo `/images/vertex-wallpaper-dark.png` y una paleta optimizada para modo oscuro, lo que respalda la legibilidad en todos los fondos.

---

## 6. Registrar los problemas encontrados
**Estado:** ✅ Verificado y documentado

A continuación los hallazgos registrados durante la auditoría técnica:

### 🔴 Jerarquía de encabezados (3 saltos detectados)
| Archivo | Problema |
|---------|----------|
| `ProjectsIndexContent.tsx` | Salta de `&lt;h1&gt;` a `&lt;h3&gt;` en la grilla de proyectos; falta un `&lt;h2&gt;` de sección antes de las tarjetas. |
| `JobsSearchContent.tsx` | Las tarjetas de vacantes usan `&lt;h2&gt;` en lugar de `&lt;h3&gt;`, rompiendo la consistencia con Proyectos y Equipo; falta `&lt;h2&gt;` de sección. |
| `LegalPageContent.tsx` | El bloque lateral *"¿Cómo ejercer tus derechos?"* es un `&lt;h3&gt;` que aparece en el DOM antes del primer `&lt;h2&gt;` de la política. |

### 🟡 Metadatos sociales incompletos
Las páginas de **Privacidad** y **Términos** (ES/EN) no cuentan con etiquetas `openGraph` ni `twitter`. Al compartir sus URLs en LinkedIn no se generará vista previa con imagen ni descripción.

### 🟡 Código muerto
Existe un componente `AboutPageContent.tsx` con su propio `&lt;h1&gt;`, pero no está enlazado a ninguna ruta activa. No afecta producción, pero se recomienda eliminarlo para limpieza del repositorio.

### 🟢 Contenido verificable
No se encontraron afirmaciones infladas ni frases tipo *"los mejores / número 1 / pioneros"* en el copy revisado. La única afirmación regulatoria específica (*"cumplimiento estricto de normas AGN y Ley 594"*) se encuentra en el caso Vertex Nexo y está documentada como contenido verificable.
