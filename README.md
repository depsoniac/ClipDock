# Mira Media Studio

**Mira Media Studio** es una mesa de trabajo multimedia para escritorio: analiza enlaces compatibles, descarga videos, convierte archivos, mejora imágenes/video con IA local y puede enviar resultados directo a Adobe Premiere Pro mediante un puente CEP.

<p align="center">
  <img src="docs/assets/mira-ui-preview.svg" alt="Vista previa de Mira Media Studio" width="920">
</p>

<p align="center">
  <a href="#inicio-rápido">Inicio rápido</a> ·
  <a href="#funciones">Funciones</a> ·
  <a href="#capturas--interfaz">Interfaz</a> ·
  <a href="#uso-responsable">Uso responsable</a>
</p>

---

## Qué es

Mira junta en una sola app lo que normalmente queda regado entre descargadores, convertidores, carpetas temporales, scripts de FFmpeg y herramientas de IA. La idea es simple: pegar un enlace o soltar archivos, elegir una salida limpia y dejar que la cola haga el resto.

> Pensado para creadores, editores y flujos donde el contenido termina en Premiere, After Effects, redes, thumbnails o archivos finales listos para entregar.

## Funciones

### Descargas desde enlaces compatibles

- Análisis de enlaces usando el motor de descarga local.
- Sesión actual con varios elementos preparados.
- Ajuste universal para aplicar una misma receta a toda la sesión.
- Modo **Sin recodificar** como valor predeterminado para descargar más rápido cuando la calidad ya existe.
- Soporte para portada, subtítulos, fragmentos por tiempo y envío a Adobe.

### Conversión y recorte

- Taller local para video/audio.
- Recorte por inicio/final.
- Salidas rápidas como H.264, H.265, ProRes, GIF, MP3 y WAV.
- Modo manual con contenedor, códecs, CRF/calidad, velocidad, resolución y FPS.

### Mejorar con IA

- Laboratorio de imagen con sesión actual, pegado con `Ctrl + V` y procesamiento por lote.
- Escalado con IA: Real-ESRGAN, Waifu2x, RealSR o SRMD según modelos instalados.
- Eliminación de fondo con modelos tipo U²-Net / IS-Net.
- Formatos de salida: PNG, JPEG, WebP, AVIF, TIFF y PDF.
- Control de tamaño, lienzo, metadatos, fondo y calidad.

### Cola de trabajos

- Progreso visual por trabajo.
- Pausar, reanudar o saltar elementos sin detener toda la cola.
- Carpeta de salida centralizada.
- Acciones individuales o globales para enviar resultados a Premiere.

### Ajustes y componentes

- Instalación bajo demanda de FFmpeg, Deno, Poppler, Inkscape y modelos IA.
- Componentes guardados en `Documentos/Mira Media Studio/Componentes`.
- Modelos guardados en `Documentos/Mira Media Studio/Modelos`.
- Cookies desde archivo `cookies.txt` o perfil de navegador.
- Panel preparado para actualizaciones por GitHub Releases o manifiesto propio.

## Capturas / interfaz

La landing incluida en `docs/index.html` usa una maqueta visual del diseño real de la app y está lista para publicarse con **GitHub Pages**.

<p align="center">
  <img src="docs/assets/mira-workflow.svg" alt="Flujo de trabajo de Mira Media Studio" width="920">
</p>

## Inicio rápido

Requisitos generales:

- Windows 10/11 recomendado.
- Node.js instalado.
- Python 3.11 o compatible con las dependencias del motor.
- FFmpeg y componentes externos instalables desde la propia app.

```powershell
# Instalar dependencias iniciales
./setup.ps1

# Abrir la app
npm start
```

También puedes usar:

```powershell
ARRANCAR.bat
```

En el primer inicio, Mira prepara dependencias y después abre la interfaz.

## Integración con Adobe Premiere

Mira incluye un panel CEP mínimo en la carpeta `adobe-extension`.

1. Ejecuta la app para iniciar el puente local.
2. Copia `adobe-extension` al directorio de extensiones CEP con el nombre `com.mira.media`.
3. Abre Premiere Pro.
4. Ve a **Ventana > Extensiones > Mira Media**.

El puente usa Socket.IO local en `127.0.0.1:7788`.

## Estructura recomendada

```text
Mira Media Studio/
├─ backend/              # API local y gestión de componentes/modelos
├─ engine/               # Media Core: descarga, conversión, IA y cola
├─ renderer/             # Interfaz Electron
├─ adobe-extension/      # Panel CEP para Premiere
├─ docs/                 # Página visual para GitHub Pages
├─ tools/                # Scripts auxiliares
├─ main.js               # Proceso principal Electron
└─ package.json
```

## GitHub Pages

Para publicar la página visual:

1. Sube la carpeta `docs/` al repo.
2. En GitHub entra a **Settings > Pages**.
3. En **Build and deployment**, elige **Deploy from a branch**.
4. Selecciona la rama principal y la carpeta `/docs`.
5. Guarda.

Tu página quedará como el sitio del proyecto.

## Uso responsable

Mira debe usarse para contenido propio, material con permiso, archivos internos, recursos con licencia compatible o fuentes donde la descarga esté permitida. El proyecto no está pensado para evadir restricciones, DRM, pagos, ni derechos de autor.

## Estado

Versión base revisada: **0.5.11**.

- Funcional: análisis de URL, descarga, cola, conversión, imagen con IA y ajustes.
- Funcional: organización de componentes/modelos en Documentos.
- Preparado: actualizaciones por manifiesto/GitHub Releases.
- En progreso recomendado: empaquetado instalable, firma de app, licencia pública y capturas reales finales.

## Licencia

Agrega un archivo `LICENSE` antes de publicar. Si quieres que sea open-source simple, MIT suele ser una opción cómoda; si quieres obligar a que forks públicos mantengan cambios abiertos, revisa AGPL. También conviene incluir avisos de licencias para binarios/modelos externos que se descargan bajo demanda.
