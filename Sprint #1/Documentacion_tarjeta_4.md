# Respuesta a Subtareas — Revisar la adaptación responsive
## Tarjeta 4: Vertex Portal Web

&gt; **Objetivo:** Comprobar que el sitio conserve una presentación legible y funcional en móvil, tableta y escritorio, sin desplazamiento horizontal involuntario, desbordamiento ni problemas de distribución.

---

## 1. Revisar la página de inicio
**Rutas:** `/es/` · `/en`

| Punto de verificación | Estado | Observación |
|-----------------------|--------|-------------|
| Sin scroll horizontal en 360 px | ✅ Verificado | Sin desbordamiento. |
| Sin scroll horizontal en 768 px | ✅ Verificado | Sin desbordamiento. |
| Sin scroll horizontal en 1024 px | ✅ Verificado | Sin desbordamiento. |
| Sin scroll horizontal en 1440 px | ✅ Verificado | Sin desbordamiento. |
| Botones y CTA accesibles (táctil/mouse) | ✅ Verificado | Todos los CTA responden correctamente. |
| Texto legible sin zoom forzado | ✅ Verificado | Tipografía legible en todos los breakpoints. |
| Imágenes y video no desbordan contenedor | ✅ Verificado | Contenido multimedia contenido correctamente. |
| Footer se apila correctamente en móvil | ✅ Verificado | Footer adapta su layout sin pérdida de información. |

---

## 2. Revisar la página de servicios
**Rutas:** `/es/nuestra-oferta` · `/es/servicios/*`

| Punto de verificación | Estado | Observación |
|-----------------------|--------|-------------|
| Grid de servicios se adapta a 1 col (360 px) / 2-3 col (768 px+) | ✅ Verificado | Layout responsive correcto. |
| Tarjetas de servicio no se cortan ni desbordan | ✅ Verificado | Tarjetas contenidas dentro de sus límites. |
| Sin scroll horizontal en 360, 768, 1024, 1440 px | ✅ Verificado | Ningún desplazamiento lateral involuntario. |
| Botones "Lo que hacemos" y CTA funcionan en táctil | ✅ Verificado | Botones táctiles operativos. |
| Imágenes de servicios escalan proporcionalmente | ✅ Verificado | Sin distorsión ni recortes extraños. |

---

## 3. Revisar la página de proyectos
**Rutas:** `/es/proyectos` · `/es/proyectos/*`

| Punto de verificación | Estado | Observación |
|-----------------------|--------|-------------|
| Grilla de proyectos responsive (1 col móvil / 2-3 col desktop) | ✅ Verificado | Adaptación de columnas correcta. |
| Tarjetas de proyecto mantienen ratio de imagen | ✅ Verificado | Imágenes conservan proporción. |
| Sin scroll horizontal en 360, 768, 1024, 1440 px | ✅ Verificado | Sin desbordamiento horizontal. |
| Botones "Ver proyecto", "Siguiente/Anterior" son táctiles | ✅ Verificado | Área de toque adecuada. |
| Página de detalle de proyecto no desborda en móvil | ✅ Verificado | Contenido contenido en viewport. |

---

## 4. Revisar la página de equipo
**Rutas:** `/es/equipo` · `/es/team/`

| Punto de verificación | Estado | Observación |
|-----------------------|--------|-------------|
| Fotos de equipo se reordenan correctamente en móvil | ✅ Verificado | Layout adaptativo sin problemas. |
| Sin scroll horizontal en 360, 768, 1024, 1440 px | ✅ Verificado | Sin desplazamiento lateral. |
| Textos de cargo/nombre no se truncan de forma extraña | ✅ Verificado | Texto legible y completo. |
| Botón "Contactar equipo" es clickeable en táctil | ✅ Verificado | CTA operativo en todos los tamaños. |

---

## 5. Revisar la página de contacto
**Rutas:** `/es/contacto` · `/es/contact`

| Punto de verificación | Estado | Observación |
|-----------------------|--------|-------------|
| Formulario de contacto no desborda en 360 px | ✅ Verificado | Formulario contenido correctamente. |
| Campos de input son táctiles y legibles en móvil | ✅ Verificado | Inputs accesibles y legibles. |
| Sin scroll horizontal en 360, 768, 1024, 1440 px | ✅ Verificado | Sin desbordamiento. |
| Botón "Hablemos de tu proyecto" se ve completo | ✅ Verificado | CTA visible e intacto. |
| Datos de contacto (email, teléfono) son clickeables en móvil | ✅ Verificado | Enlaces de contacto funcionales. |

---

## 6. Probar anchos aproximados de 360, 768, 1024 y 1440 píxeles

| Ancho | Dispositivo referencia | Estado general |
|-------|------------------------|----------------|
| 360 px | iPhone SE / Galaxy S8 | ✅ Verificado |
| 768 px | iPad Mini / tablet vertical | ✅ Verificado |
| 1024 px | iPad horizontal / tablet landscape | ✅ Verificado |
| 1440 px | Laptop estándar / desktop | ✅ Verificado |

**Checklist por breakpoint:**
- [x] No hay scroll horizontal involuntario.
- [x] El contenido no se sale de la pantalla.
- [x] Las fuentes son legibles sin hacer zoom.
- [x] Los botones y enlaces tienen área de toque adecuada en móvil.
- [x] Las imágenes no se pixelan ni desbordan sus contenedores.

---

## 7. Revisar el menú móvil

| Punto de verificación | Estado | Observación |
|-----------------------|--------|-------------|
| El menú hamburguesa se despliega correctamente en 360 px | ✅ Verificado | Menú móvil operativo. |
| Los enlaces del menú son clickeables en táctil | ✅ Verificado | Navegación táctil funcional. |
| El menú cubre toda la pantalla o se despliega como drawer | ✅ Verificado | Drawer desplegable correcto. |
| Se puede cerrar el menú (botón X o tocar fuera) | ✅ Verificado | Cierre del menú funcional. |
| Las rutas del menú coinciden con las rutas principales validadas en QA | ✅ Verificado | Enlaces correctos. |
| No hay elementos del menú tapados por la barra del navegador móvil | ✅ Verificado | Sin solapamientos. |

&gt; **Nota en 1440 px:** El menú móvil desaparece y se visualiza el menú de escritorio. Esto es el **comportamiento esperado** por el breakpoint de responsive; no es un hallazgo negativo.

---

## 8. Revisar márgenes y espacios entre secciones

| Punto de verificación | Estado | Observación |
|-----------------------|--------|-------------|
| Márgenes laterales consistentes en todas las páginas | ✅ Verificado | Padding/margen uniforme. |
| Espaciado vertical entre secciones no es excesivo ni insuficiente | ✅ Verificado | Espaciado proporcional y armónico. |
| No hay secciones pegadas sin padding en móvil | ✅ Verificado | Separación clara entre bloques. |
| El footer tiene margen superior claro respecto al contenido | ✅ Verificado | Footer bien delimitado. |
| Las secciones de ancho completo no generan scroll lateral | ✅ Verificado | Full-width contenido correctamente. |

---

## Resumen de la tarjeta 4

| # | Subtarea | Estado |
|---|----------|--------|
| 1 | Revisar la página de inicio | ✅ Verificado |
| 2 | Revisar la página de servicios | ✅ Verificado |
| 3 | Revisar la página de proyectos | ✅ Verificado |
| 4 | Revisar la página de equipo | ✅ Verificado |
| 5 | Revisar la página de contacto | ✅ Verificado |
| 6 | Probar anchos de 360, 768, 1024 y 1440 px | ✅ Verificado |
| 7 | Revisar el menú móvil | ✅ Verificado |
| 8 | Revisar márgenes y espacios entre secciones | ✅ Verificado |

**Conclusión general:** El sitio pasa la auditoría de adaptación responsive en todos los breakpoints evaluados. No se detectaron desbordamientos, scroll horizontal involuntario ni problemas de legibilidad. El cambio de menú móvil a menú de escritorio en 1440 px corresponde al comportamiento esperado del breakpoint de responsive.
