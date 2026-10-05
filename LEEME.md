# MinervA4

**Un único archivo HTML que convierte Markdown —o un documento de Word— en un PDF A4 con la identidad de la marca.**
Sin instalar nada, sin compilar, sin servidor y sin cuenta. Se abre con doble clic y funciona sin conexión.

[English](README.md) · [Guía de uso (ES)](playground/documents/template_guide_a4.es.md)

---

## Pruébalo

1. Abre **`MinervA4.html`** en el navegador y pulsa **Ver un ejemplo**.
2. En **Marca**, carga `style-guides/acme-corporativo-style.yaml`. Cambia a
   `acme-editorial-style.yaml` y cambia el documento entero —títulos, tablas,
   pies y diagramas— sin tocar un solo carácter del Markdown.

Después prueba la demostración de verdad, que es para lo que está
`playground/`:

1. Arrastra `playground/documents/template_guide_a4.es.md` sobre la ventana.
2. Añade `playground/data/es/cifras-T3-2026.json`. Los últimos capítulos de la
   guía se rellenan solos con esas cifras.
3. Apunta **Añadir una carpeta de imágenes** a `playground/images/`.
4. Y ahora lo interesante: carga `playground/data/es/cifras-T4-2026.json`.
   **Sin tocar una letra del texto**, cambian las cifras, cambia el color de
   las cajas de aviso, cambia el veredicto del trimestre y cambian las
   recomendaciones del final. El tercer trimestre cumplió el objetivo y el
   cuarto no, y el documento lo sabe.

## Qué hace

- **El contenido entra de tres maneras.** Un archivo `.md`, un **documento de
  Word** (el texto, los títulos, las listas, las tablas y las imágenes pasan;
  el estilo lo pone la marca) o pegado directamente en el editor.
- **La marca vive en un archivo YAML.** Colores, tipografías, márgenes,
  portada, índice y pie —y además la orientación de la página, el modo
  presentación y el fondo de la hoja—. El mismo texto se entrega hoy con una
  marca y mañana con otra. Sin YAML cargado, la herramienta usa sus valores
  por defecto.
- **Las cifras se citan, no se copian.** Carga un `.xlsx`, un `.csv` o un
  `.json` y el documento referencia los valores. Suelta el archivo del
  trimestre siguiente y todo se recompone. Un selector de campos recorre el
  árbol entero y escribe los marcadores por ti, incluidas las secciones
  condicionales y los bloques repetidos por fila. Se pueden cargar varios
  orígenes a la vez.
- **El control de la página, desde el texto.** Saltos de página, giros a
  apaisado, justificación, cajas de aviso y bloques a varias columnas —cada uno
  con su botón en la barra del editor—.
- **Diagramas de Mermaid y fórmulas de KaTeX**, recoloreados a la paleta de la
  marca y con el contraste de cada caja comprobado.
- **El tamaño de la imagen se declara donde se usa la imagen**: `{width=60%}`,
  `{width=320px}`, `{width=80mm height=40mm}`.
- **Seis idiomas de interfaz**: castellano, inglés, francés, alemán, italiano y
  polaco. El idioma de la interfaz y el del documento se eligen por separado, y
  el formato de número sigue al del documento.

## Qué hay aquí

| Ruta | Qué es |
|---|---|
| `MinervA4.html` | La herramienta. El único archivo que de verdad hace falta. |
| `index.html` | Un redireccionamiento de una línea, para que la carpeta abra en la herramienta. |
| `style-guides/` | Dos guías de marca de ejemplo, en YAML. |
| `logos/` | Un logotipo de ejemplo para el panel **Marca**. |
| `playground/documents/` | La guía de uso en tres idiomas, más ejemplos sueltos. |
| `playground/images/` | Diez imágenes, cada una en un formato distinto. |
| `playground/data/` | Las mismas cifras como `.json`, `.csv` y `.xlsx`, en `es`, `en` y `de`. |

**Todo lo que hay aquí es ficticio**: la marca es ACME, y no hay ni una cifra,
ni un nombre, ni una dirección de una empresa real.

### Las guías

`playground/documents/template_guide_a4.{es,en,de}.md` son el documento único
de demostración: cada una explica la herramienta y, en sus dos últimos
capítulos, la demuestra en vivo —cifras conectadas al archivo de datos,
condiciones, un bucle por filas, tablas que se rellenan solas, la moneda, y las
imágenes a tamaño declarado—. Abre una con la propia herramienta: está escrita
para leerse maquetada.

Las tres llevan las mismas cifras. Lo único que cambia son los textos, para que
se puedan leer una al lado de otra y se vea el formato de número siguiendo al
idioma del documento: `4.310.000` en castellano y en alemán, `4,310,000` en
inglés, sin que nadie configure nada.

### Los datos

De cada idioma y cada trimestre salen los tres formatos que la herramienta lee:

| | qué demuestra |
|---|---|
| `.json` | el libro entero, con sus tres conjuntos de datos |
| `.csv` | lo que exporta una hoja de cálculo: una tabla y ya |
| `.xlsx` | un libro de tres pestañas, para el selector de conjuntos |

Los nombres de los campos **no se traducen** —`revenue`, `margin`,
`on_time`—: son el nombre del dato, y la sintaxis canónica es inglesa. Lo que
se traduce son los valores, que es lo que se lee impreso.

### Las imágenes

Diez, y cada una pone a prueba una cosa distinta del maquetador: que un
vectorial escale sin pixelarse, que un PNG con transparencia deje ver el fondo,
que un sello pequeño no se estire, que un BMP grande no reviente el archivo,
que el AVIF —el formato más nuevo— entre.

## Imprimir

Usa **Imprimir en PDF**, con los márgenes en *Ninguno*, la escala al 100 % y los
**gráficos de fondo activados**. Los márgenes de la página los pone la guía de
marca, no el navegador.

## Privacidad

Nada sale del ordenador. No hay ninguna llamada a la red, ni analítica, ni
cuenta: el archivo lee lo que le des en el navegador y lo compone ahí. Es
también por eso que pesa unos 5 MB —Mermaid, KaTeX, el lector de hojas de
cálculo y las tipografías van todos dentro—.

## Tu propia marca

Las guías de estilo que hay aquí usan una marca inventada. Copia cualquiera de
las dos y cámbiale los colores y las tipografías. La guía real de tu empresa
déjala en tu equipo: el `.gitignore` ignora `style-guides/private-*` y
`logos/private-*`, así que puedes trabajar con ella en esta carpeta sin
publicarla por descuido.

## Licencia

MIT — ver [LICENSE](LICENSE).
