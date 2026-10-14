# Brief estratégico · Landing Oferta Relámpago LATAM

**Marketing Analytics · Magíster** · Taller: del objetivo de negocio al sitio medible

> Proyecto académico ficticio. El caso usa a LATAM como marca de referencia; no está afiliado a LATAM Airlines Group y las tarifas son ilustrativas.

---

## 0. Equipo y proyecto

| Campo | Respuesta |
| --- | --- |
| Integrantes | Clément Labarthe |
| Nombre del proyecto | Landing Oferta Relámpago |
| Negocio (real o ficticio) | Ficticio: campaña de "Oferta Relámpago" de 48 horas de una aerolínea (caso LATAM) |
| URL final del sitio | https://cru123.github.io/landing-oferta-relampago/ |

## 1. Contexto de negocio

**¿Qué vende o qué ofrece la organización?**
Pasajes aéreos ida y vuelta desde Santiago. En esta campaña, dos rutas internacionales (Santiago–Río de Janeiro y Santiago–Cusco) con tarifa rebajada por 48 horas, pagables en pesos o en millas LATAM Pass.

**¿Qué problema del cliente resuelve?**
El cliente ya buscó estos destinos pero no compró, normalmente por precio o por indecisión sobre el momento. La oferta le da un precio menor y una razón concreta para decidir ahora.

**¿Por qué existe este sitio? ¿Qué cambiaría en el negocio si funciona bien?**
El sitio es el destino de un correo y de publicaciones de remarketing. Su trabajo es convertir búsquedas abandonadas en intención de reserva. Si funciona, la aerolínea recupera ventas de clientes que ya estaban cerca de comprar, a un costo de adquisición menor que con un cliente nuevo.

## 2. Modelo de medición

| Nivel | Pregunta guía | Respuesta |
| --- | --- | --- |
| **Objetivo de negocio** | ¿Para qué existe el sitio? | Generar demanda: recuperar reservas de clientes que buscaron Río o Cusco y no compraron. |
| **Meta del sitio** | ¿Qué conducta concreta sirve al objetivo? | Que el visitante haga clic en "Reservar ahora" en alguno de los dos destinos (simula el inicio de la compra). |
| **KPI** | ¿Qué indicador muestra si la meta se cumple? | Tasa de sesiones con al menos un evento `clic_cta_principal` (= "tasa de eventos clave de la sesión" en GA4). |
| **Target** | ¿Qué valor sería éxito en una semana? ¿Con qué fundamento? | **≥ 15 %** de las sesiones con clic, con un mínimo de 50 sesiones. Fundamento: el *Conversion Benchmark Report* de Unbounce sitúa la mediana de conversión de landings cerca de 6–7 %, pero esa cifra mide conversiones completas (formulario o compra). Un clic en el CTA es una microconversión con menos fricción, y el tráfico viene de contactos cercanos que reciben el enlace directo, por lo que suponemos que puede duplicarla. Es un supuesto explícito para contrastar. |
| **Segmentos** | ¿Qué grupos queremos comparar? | (1) Canal: `utm_source` WhatsApp, Instagram, LinkedIn y correo. (2) Dispositivo: móvil vs. escritorio. (3) Ubicación del clic: parámetro `ubicacion` (`ofertas` vs. `cierre`). (4) Destino elegido: parámetro `destino` (`rio_de_janeiro` vs. `cusco`). |

## 3. Audiencia

| Campo | Respuesta |
| --- | --- |
| ¿Quién es el visitante principal? | Adulto de 25 a 45 años en Chile, con ingresos medios, que viaja por turismo una o dos veces al año. Ya conoce el destino que buscó; no necesita que le expliquen qué es Río o Cusco. |
| ¿Qué tarea intenta resolver? | Saber si el precio ahora es lo bastante bueno como para decidir el viaje. |
| ¿Desde dónde llega? | Correo de remarketing y mensajes por WhatsApp o redes sociales con el enlace de la oferta. |
| ¿Qué dispositivo usará? | Mayoritariamente móvil (abre el correo o el mensaje en el teléfono). |
| Principales objeciones o dudas | (1) "¿Es realmente más barato?" (2) "¿Y si después cambio de planes?" (3) "¿Puedo pagar con mis millas?" (4) "¿Tengo que decidir ya?" |

## 4. Mensaje

**Propuesta de valor en una sola frase:**
Los dos destinos que ya buscaste, a un precio exclusivo que solo dura 48 horas.

**Tres argumentos de apoyo** (en orden de importancia para la audiencia):

1. Precio visiblemente menor: tarifa anterior tachada, precio de oferta y monto del ahorro.
2. Personalizado: son exactamente los destinos que el cliente buscó, sin tener que buscar de nuevo.
3. Respaldo de la aerolínea: acumulación de millas LATAM Pass, flexibilidad en la compra y la red más conectada de Sudamérica.

**Evidencia o prueba que reduce el riesgo percibido:**
Precio anterior vs. precio de oferta con el ahorro explícito, opción de pago en millas y beneficios de flexibilidad. *Supuesto: negocio ficticio; las tarifas y equivalencias en millas son ilustrativas.*

## 5. Acción y medición

| Campo | Respuesta |
| --- | --- |
| CTA principal (texto exacto) | "Reservar ahora" |
| ¿Qué ocurre al hacer clic? | Se abre una página de gracias dentro del mismo sitio que simula la confirmación de la reserva del destino elegido. No pide datos. |
| URL de destino del CTA | `#gracias` (sección interna de la misma página) |
| CTA secundario | "Ver mis 2 ofertas", en el hero: baja a la sección de ofertas. |
| Nombre del evento en GA4 | `clic_cta_principal`, con los parámetros `ubicacion` (id de la sección) y `destino` (`rio_de_janeiro` / `cusco`). |
| ¿Cómo se relaciona con el KPI? | Cada clic registra el evento; marcado como evento clave, GA4 calcula la tasa de sesiones con evento clave, que es directamente el KPI. |

**Nota sobre el destino interno:** la guía pide que el CTA abra una pestaña nueva para que la página no se cierre antes de enviar el evento. Aquí el CTA no sale de la página (abre la sección de gracias en la misma vista), así que el evento se envía igual sin riesgo de perderse. Se eligió así porque el sitio es estático y no puede procesar pagos.

## 6. Arquitectura de información

| Orden | Sección | Propósito | Contenido principal | ¿Incluye CTA? |
| --- | --- | --- | --- | --- |
| 1 | Hero (`#hero`) | Que en 3 segundos entienda que hay una oferta personal y que vence. | Titular personalizado, subtítulo, cuenta regresiva de 48 h, aviso de expiración. | Sí (secundario: "Ver mis 2 ofertas") |
| 2 | Ofertas (`#ofertas`) | Mostrar los dos destinos con el ahorro concreto y pedir la acción. | 2 tarjetas: foto, destino, ruta, precio anterior tachado, precio de oferta, ahorro, millas. | Sí (principal ×2) |
| 3 | Beneficios (`#beneficios`) | Responder "¿y si cambio de planes?" y "¿puedo usar millas?". | Acumulación de millas, flexibilidad, red de destinos. | No |
| 4 | Cierre (`#cierre`) | Recordar la urgencia y dar una segunda oportunidad de acción a quien siguió bajando. | Horas restantes y un botón por destino. | Sí (principal ×2) |
| 5 | Pie de página | Transparencia. | Aviso de proyecto académico, uso de Analytics, créditos de fotos. | No |

**Revisión de la estructura:**
- **¿Se entiende sin scroll?** Sí: titular, subtítulo y contador están arriba.
- **¿Se responden las objeciones antes de pedir la acción?** Precio y ahorro, sí. Flexibilidad y millas se muestran en la tarjeta (millas) y en Beneficios, justo antes del segundo CTA.
- **¿El CTA principal aparece al inicio y al final?** Al final, sí (Cierre). Al inicio, el hero tiene el CTA secundario que lleva a las tarjetas; en escritorio las tarjetas quedan visibles casi sin scroll. No se puso "Reservar ahora" en el hero porque reservar exige elegir destino primero.
- **¿Hay secciones sin propósito?** Se eliminaron los enlaces de pie ("Gestiona tu reserva", etc.) del correo original porque no llevaban a ninguna parte.

**Wireframe:** [`wireframe.svg`](wireframe.svg)

### Revisión crítica del wireframe (Prompt 1)

Diagnóstico: el orden lleva de comprensión (hero) a evaluación (ofertas) a refuerzo (beneficios) y de vuelta a la acción (cierre). Es una secuencia corta y coherente con un visitante que ya conoce los destinos.

Recomendaciones priorizadas:

1. **Mostrar el ahorro en pesos, no solo el precio tachado.** Responde la objeción n.º 1 ("¿es realmente más barato?") con una cifra concreta. *Aceptada:* se agregó "Ahorras $X".
2. **Agregar un CTA de cierre.** En móvil, quien baja hasta beneficios ya pasó las tarjetas; sin otro botón se pierde la acción. *Aceptada:* sección Cierre con un botón por destino.
3. **Hacer que el contador avance de verdad.** Un contador fijo en "47:59:59" resta credibilidad. *Aceptada:* cuenta 48 h desde la primera visita del navegador.
4. **Medir qué destino se elige.** Sin esto no se puede comparar Río vs. Cusco. *Aceptada:* parámetro `destino` en el evento.
5. **Quitar la barra con número de socio y millas.** En un sitio público serían datos personales o inventados. *Aceptada:* se reemplazó por un saludo genérico.

## 7. Restricciones del ejercicio

- [x] Una sola página (`index.html`) con HTML, CSS y JavaScript en el mismo archivo. Las fotos van aparte, en `img/`.
- [x] Sitio público sin información confidencial ni datos reales de clientes.
- [x] Sin formularios propios: el CTA abre una página de gracias que no pide datos.
- [x] Sin logos de terceros: la marca aparece solo como texto. Fotos de Unsplash bajo su licencia gratuita, con crédito.
- [x] Contenido honesto: aviso visible de proyecto académico ficticio, no afiliado a LATAM.

## 8. Hipótesis a validar con datos

> Creemos que **adultos en Chile que ya buscaron Río o Cusco**, al llegar desde **WhatsApp**, harán clic en **"Reservar ahora"** porque **la cuenta regresiva de 48 horas y el ahorro explícito en pesos eliminan la razón para postergar la decisión**. Lo sabremos si la **tasa de sesiones con `clic_cta_principal`** alcanza **≥ 15 %** durante la semana de difusión, y si WhatsApp supera a los demás canales en esa tasa.

## Checklist antes de pasar al wireframe

- [x] El objetivo de negocio se entiende sin explicación adicional.
- [x] El KPI se puede medir con un evento del sitio (`clic_cta_principal`).
- [x] El target tiene fundamento (benchmark de Unbounce + supuesto explícito).
- [x] El CTA principal está redactado y tiene destino (`#gracias`).
- [x] La arquitectura tiene 5 secciones, cada una con propósito.
- [x] La hipótesis es falsable con los datos que se recogerán.

---

## Difusión con enlaces UTM

URL base: `https://cru123.github.io/landing-oferta-relampago/`

| Canal | URL con UTM |
| --- | --- |
| WhatsApp | https://cru123.github.io/landing-oferta-relampago/?utm_source=whatsapp&utm_medium=mensajeria&utm_campaign=taller_ma |
| Instagram | https://cru123.github.io/landing-oferta-relampago/?utm_source=instagram&utm_medium=social&utm_campaign=taller_ma |
| LinkedIn | https://cru123.github.io/landing-oferta-relampago/?utm_source=linkedin&utm_medium=social&utm_campaign=taller_ma |
| Correo | https://cru123.github.io/landing-oferta-relampago/?utm_source=correo&utm_medium=email&utm_campaign=taller_ma |

**Registro de difusión** (completar al compartir):

| Canal | Fecha | Audiencia aproximada | URL con UTM |
| --- | --- | --- | --- |
|  |  |  |  |
|  |  |  |  |

## Fuentes

- Kaushik, A. *Digital Marketing and Measurement Model*. Occam's Razor.
- Unbounce. *Conversion Benchmark Report*.
- Google Analytics Help. *[GA4] Mark events as key events*.
