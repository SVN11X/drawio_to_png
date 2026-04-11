# .drawio → PNG Converter

Una herramienta web minimalista y de alto rendimiento para convertir archivos de **diagrams.net** (`.drawio` o `.xml`) a imágenes **PNG** de alta resolución. 

A diferencia de otros convertidores, esta herramienta utiliza el **motor de renderizado oficial de draw.io** a través de su API de comunicación entre ventanas (`postMessage`), garantizando que el resultado sea 100% idéntico al que obtendrías en la aplicación de escritorio o web oficial.

## ✨ Características

* **Procesamiento por lotes:** Sube múltiples archivos simultáneamente.
* **Fondo personalizable:** Elige entre fondo Blanco, Oscuro o Transparente antes de exportar.
* **Renderizado de alta calidad:** Exportación con escala $2x$ para mayor nitidez.
* **Salida en ZIP:** Empaqueta automáticamente todas tus imágenes convertidas en un solo archivo comprimido.
* **Logs en tiempo real:** Consola integrada para monitorear el estado de cada conversión.
* **Sin servidor (Serverless):** La lógica de la aplicación corre enteramente en el cliente (tu navegador).

## 🛠️ Tecnologías utilizadas

* **HTML5 / CSS3:** Interfaz moderna con tema oscuro y variables CSS.
* **Vanilla JavaScript:** Lógica ligera sin dependencias pesadas de framework.
* **JSZip:** Para la generación de archivos comprimidos en el lado del cliente.
* **Draw.io Embed API:** Uso de un `iframe` oculto conectado a `embed.diagrams.net` para el renderizado profesional.

## 🚀 Cómo usarlo

1.  **Carga:** Arrastra tus archivos `.drawio` al área designada o haz clic para buscarlos.
2.  **Configura:** Selecciona el color de fondo deseado en el selector.
3.  **Convierte:** Haz clic en **"Convertir a PNG"**. Verás el progreso en la caja de salida (*output*).
4.  **Descarga:** Una vez finalizado, el botón **"Descargar ZIP"** se activará para que guardes tus imágenes.

## 🔒 Privacidad y Seguridad

La privacidad es una prioridad en este proyecto:
* **Sin base de datos:** No almacenamos tus archivos; todo ocurre en la memoria temporal de tu navegador.
* **Sin trackers:** No incluye Google Analytics, cookies ni píxeles de seguimiento.
* **Transparencia de datos:** Para poder renderizar el PNG, el XML del diagrama se envía de forma temporal al servidor oficial de JGraph Ltd (`embed.diagrams.net`). Es el mismo proceso que ocurre al usar la versión oficial de la herramienta.

## 🧠 Detalles Técnicos

El flujo de conversión sigue esta arquitectura:
1.  El navegador lee el archivo local mediante `FileReader`.
2.  Se instancia un `iframe` apuntando a la URL de exportación de draw.io.
3.  Se envía el XML mediante un `postMessage` con la acción `load`.
4.  Se solicita una acción `export` con formato `png` y el `bgColor` seleccionado.
5.  El `iframe` devuelve el `dataURL` de la imagen, que es capturado y procesado por el script principal.

## 📄 Licencia

Este proyecto es de código abierto. Siéntete libre de clonarlo, modificarlo y adaptarlo a tus necesidades.

---

### Notas de instalación
No requiere instalación. Simplemente abre el archivo `index.html` en cualquier navegador moderno.

> [!TIP]
> Si trabajas con diagramas altamente confidenciales y tu política de empresa prohíbe conexiones externas, se recomienda utilizar la aplicación **draw.io Desktop**, que permite exportaciones 100% offline.
