# Documento de decisiones de diseño

_> Cada decisión: **qué** elegiste, **por qué**, y **qué alternativa descartaste**._
> Se evalúa la justificación, no la longitud. Máximo 2 páginas en la Fase 1.

## Ruta de trabajo

- [ ] Ruta A · Figma (enlace con permiso de lectura: …)
- [x] Ruta B · VS Code (diseño directamente en `guia.html`)

## 1. Color (RA1 · CE b)

- **Tono de acento de la ficha y cómo has obtenido la escala (50 … 950):** 112°

- **Por qué el acento de texto/fondo es el 700 en claro y el 400 en oscuro (o el que elijas):** Porque se leen mejor en cada tema.

- **Tokens semánticos añadidos y para qué:** Añadí `error`, `error-tenue`, `aviso` y `aviso-tenue` para mostrar errores y avisos.

- **Pares de contraste añadidos a `$pares-contraste`:** Añadí los pares de error y aviso con sus fondos para asegurar un contraste mínimo de 4,5:1.

## 2. Tipografía (RA1 · CE b)

- **Familia elegida y por qué (rendimiento, legibilidad, licencia):** Elegí `system-ui` porque es fácil de leer, gratuita y no necesita descargar fuentes.

- **Base y razón en móvil y escritorio. Por qué esas:** Móvil: 16 px y 1,2. Escritorio: 18 px y 1,25. Así el texto se adapta a cada pantalla.

- **Medida de línea (`max-inline-size` del párrafo en `ch`):** 65ch como medida recomendada para facilitar la lectura.

## 3. Espaciado y forma

- **Escala de espaciado y radios. Si cambias algo respecto a la plantilla, por qué:** Mantengo los espacios de 4 a 64 px y los radios de 8 y 12 px. No los cambié porque dan un aspecto uniforme.

## 4. Componentes (RA1 · CE f)

| Componente | Estados | Cómo se resuelve cada estado en CSS |
| --- | --- | --- |
| Botón | normal, hover, foco, desactivado, secundario | Uso `:hover`, `:focus-visible`, `:disabled` y `.boton--secundario`. |
| Turno | disponible, seleccionado, ocupado, foco | Uso `:has()`, bordes diferentes y texto para cada estado. |
| Contador de invitados | normal, seleccionado, foco | Cuatro radios del 0 al 3, con Flexbox y `:has()`. |
| Aviso de pago | normal | Fondo claro, borde destacado y datos del pago. |

## 5. Comparativa de tecnologías (RA1 · CE e · RA2 · CE i)

| Criterio | Figma | Penpot | Diseño en código |
| --- | --- | --- | --- |
| Coste / licencia | Gratis con límites | Código abierto | Gratis |
| Traslado a código (handoff) | Hay que pasarlo a HTML/CSS | Hay que pasarlo a HTML/CSS | Ya está en código |
| Mantenimiento del sistema | Componentes y variables | Componentes y variables | SCSS y tokens |

| Criterio | Sass + CSS propio | CSS nativo sin preprocesador | Bootstrap / Tailwind |
| --- | --- | --- | --- |
| Tokens y temas | Mapas y variables | Variables CSS | Configuración propia |
| Peso del CSS final | Solo nuestro CSS | Ligero | Depende del uso |
| Control de la cascada | `@layer` y BEM | `@layer` | Clases del framework |

**Decisión y motivo:** Elegí Sass + CSS propio porque puedo organizar mejor los estilos y controlar el diseño. Descarté Bootstrap y Tailwind porque quería crear mis propios componentes.