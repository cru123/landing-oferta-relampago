# Auditoría y explicación del sitio

## Auditoría antes de publicar (Prompt 4)

Revisión de `index.html` frente al objetivo de negocio (recuperar reservas de quienes buscaron Río o Cusco) y al CTA principal ("Reservar ahora"). Se probó en el navegador a 1100 px y a 375 px (móvil).

| # | Hallazgo | Severidad | Corrección |
| --- | --- | --- | --- |
| 1 | El correo de origen mostraba el número de socio y las millas de un cliente real. | Alta | Se eliminó la barra de socio; el saludo es genérico ("¡Hola, viajero!"). |
| 2 | El sitio usa la marca LATAM y podría confundirse con una oferta real. | Alta | Aviso de proyecto académico en la barra superior, en el pie y en la página de gracias. Sin logo oficial, solo texto. |
| 3 | Pie con "© LATAM Airlines Group" y enlaces que no llevaban a ninguna parte. | Media | Se quitaron: eran falsos o no servían al objetivo. |
| 4 | Contador fijo en 47:59:59: poco creíble. | Media | Ahora cuenta 48 h reales desde la primera visita del navegador. |
| 5 | Texto de la nota de gracias en #777 (contraste 4,48:1, bajo el mínimo de 4,5:1). | Media | Se cambió a #666 (5,74:1). |
| 6 | El CTA no abre una pestaña nueva, como pide la guía. | Baja | Decisión justificada: abre una sección interna, la página no se cierra y el evento se envía igual (ver BRIEF §5). |
| 7 | La página de gracias no se cierra con la tecla Escape. | Baja | Se puede cerrar con el botón "Volver a las ofertas", que recibe el foco al abrirse. No se corrige. |

Verificado sin hallazgos:

- Hay **exactamente un** `id="cta-principal"`; las otras tres repeticiones usan `class="cta-principal"`. Los cuatro botones abren la página de gracias con el destino correcto.
- **Móvil:** sin desborde horizontal (ancho de página = ancho de pantalla, 375 px). Los botones miden 48 px de alto como mínimo y las tarjetas se apilan.
- **Accesibilidad:** contraste del botón coral 4,55:1 y de los textos lila sobre azul 10,7:1. Todas las fotos tienen texto alternativo. Jerarquía de títulos: un solo `h1`, luego `h2` por sección y `h3` en tarjetas y beneficios.
- **Contenido:** no hay testimonios, clientes ni cifras presentadas como reales. Precios y millas están declarados como ilustrativos.
- **Seguridad y privacidad:** no hay formularios ni recursos externos (sin fuentes, librerías ni imágenes de otros servidores). El único script externo será la etiqueta de Google Analytics. `localStorage` solo guarda la hora en que vence el contador.

## Explicación para un gerente de marketing (Prompt 5)

**1. ¿Qué hace cada bloque del archivo?**
- **`<head>`:** datos de la página (título, descripción, ajuste para móvil). Aquí irá la etiqueta de Google Analytics.
- **`<style>`:** el diseño. Arriba están los colores de marca (`--azul`, `--coral`, etc.); luego, los estilos de cada sección. Al final, las reglas para móvil (`@media`), que apilan tarjetas y beneficios.
- **`<header>` y `<main>`:** el contenido visible, en orden: Hero, Ofertas, Beneficios, Cierre.
- **`<footer>`:** aviso académico y créditos.
- **`#gracias`:** la ventana de "reserva confirmada", oculta hasta que alguien hace clic en un CTA.
- **`<script>`:** dos funciones. (a) El contador de 48 horas. (b) Abrir la página de gracias con el nombre del destino elegido.

**2. ¿Qué tocar para cambiar…?**
- **El texto del CTA:** buscar "Reservar ahora" (aparece 4 veces) y cambiar solo el texto entre `>` y `</a>`. No tocar `id` ni `class`.
- **Los colores:** las líneas `--azul`, `--coral`, etc., al inicio de `<style>`. Al cambiarlas se actualiza todo el sitio.
- **El orden de las secciones:** mover bloques completos `<section id="…"> … </section>` dentro de `<main>`.
- **Precios:** los párrafos `class="antes"` (tachado), `class="ahora"` (oferta) y `class="ahorro"` de cada tarjeta.

**3. ¿Algo se ejecuta sin que el visitante lo vea?**
- El contador guarda en el navegador del visitante (`localStorage`) la hora de vencimiento, para no reiniciarse al recargar. No sale del navegador.
- Al instalar Google Analytics: la etiqueta registra cada visita (página, dispositivo, canal) y el script del CTA envía el evento `clic_cta_principal` con la sección y el destino. No se envía ningún dato personal.
