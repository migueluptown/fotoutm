# FotoUTM v2 – Reporte fotográfico georreferenciado (PWA para Android)

## Contenido
| Archivo | Función |
|---|---|
| `index.html` | Aplicación completa (incluye la librería pdf-lib, no depende de CDN) |
| `manifest.webmanifest` | Permite instalarla como app en Android |
| `sw.js` | Funcionamiento sin conexión (los mapas sí requieren internet) |
| `icon-192.png`, `icon-512.png` | Íconos de la app |

## Requisito técnico
La cámara, el GPS y la brújula del navegador solo funcionan en páginas servidas por **HTTPS**. Por ello la carpeta debe publicarse en un alojamiento web con HTTPS (gratuito). Abrir el `index.html` directamente desde el almacenamiento del celular no habilita esos sensores.

## Publicación gratuita en GitHub Pages (una sola vez, ~10 min, desde la PC)
1. Cree una cuenta en https://github.com (si no la tiene).
2. Botón **New repository** → nombre `fotoutm` → **Public** → **Create repository**.
3. En el repositorio: **Add file → Upload files** → arrastre los 5 archivos de esta carpeta (no la carpeta) → **Commit changes**.
4. **Settings → Pages** → *Source*: **Deploy from a branch** → *Branch*: `main` / `(root)` → **Save**.
5. Espere 1–2 minutos. La dirección será: `https://SU-USUARIO.github.io/fotoutm/`

## Instalación en el celular Android
1. Abra la dirección anterior en **Google Chrome**.
2. Acepte los permisos de **Ubicación** y **Cámara**.
3. Menú ⋮ → **Agregar a la pantalla principal / Instalar app**. Aparecerá el ícono FotoUTM.
4. En el celular active **Ubicación en modo de alta precisión** y, si la brújula marca valores erráticos, calíbrela moviendo el teléfono en forma de “8”.

## Novedades de la versión 2
- Interfaz rediseñada para uso en campo (alto contraste, botones grandes, coordenadas en letra monoespaciada). Las fuentes van incluidas: funciona sin conexión.
- Cámara con brújula: retícula central, indicador de inclinación, rosa de los vientos, linterna (si el equipo la admite) y miniatura de la última toma.
- Editor: dictado por voz de la descripción (requiere internet), frases rápidas configurables, contador de caracteres, ajuste fino del azimut (−5°, −1°, +1°, +5°, barra y «usar azimut actual»), edición de inclinación y precisión.
- Ajustes por secciones, N.° CIP del responsable, lista de frases rápidas y «Restablecer valores».
- Exportación con barra de progreso (página y teselas), botón Cancelar y miniaturas de las páginas.
- Pantalla guiada para recuperar permisos de ubicación o cámara.
- PDF: mismo esquema (datos generales → foto → dos plantas → descripción), con franja institucional, campos nuevos de Inclinación, Precisión y CIP, coordenadas en Courier y leyenda gráfica de símbolos.
- Los registros de la versión 1 se conservan al actualizar (misma base de datos local).

## Uso
1. **⚙ Ajustes** (una vez): título, entidad, proyecto, responsable, logo, escalas y mapas base de las dos vistas en planta, declinación magnética.
2. **Cámara con brújula**: muestra en pantalla Este/Norte, precisión y azimut; al disparar registra todo en ese instante. Puede tomar varias fotos seguidas.
3. **Cámara del sistema**: usa la cámara nativa (mayor calidad). Apunte primero y luego pulse el botón; el azimut se registra al pulsar.
4. **Galería**: importa fotos existentes; lee el GPS de los metadatos EXIF si existe. Si no existe, asigna la posición actual y lo advierte.
5. Toque una foto para editar lugar, descripción, coordenadas UTM (Este/Norte), altitud, azimut y fecha; botón **Vista previa de los mapas**.
6. Marque las fotos y pulse **Generar PDF A4** → **Descargar** o **Compartir** (WhatsApp, correo, Drive).

## El PDF
- Una página A4 por foto, con el formato: datos generales + logo, foto principal, dos vistas en planta (detalle y ubicación) con punto de toma, sector de visión, flecha de dirección, norte, barra de escala y escala numérica; recuadro de descripción.
- **Campos editables (formulario PDF):** Proyecto, Lugar, Responsable (con CIP), Fecha, Hora, Sistema, Este (X), Norte (Y), Altitud (Z), Azimut, Inclinación, Precisión y Descripción. Se editan con Adobe Acrobat Reader, Xodo, Foxit o el navegador de la PC.
- La escala indicada es exacta para impresión en A4 al 100 % (sin “ajustar a página”).

## Notas técnicas
- Coordenadas: WGS84, proyección UTM, zona calculada automáticamente (Cusco: 19 S; Lima: 18 S). Conversión verificada contra la librería proj4 (diferencia < 1 mm).
- Azimut: medido desde el norte, en sentido horario, en la dirección de la cámara trasera. La brújula del celular es magnética; registre en Ajustes la declinación de su zona (calculador NOAA: https://www.ngdc.noaa.gov/geomag/calculators/magcalc.shtml) para obtener azimut referido al norte verdadero. Precisión típica de una brújula de celular: ±5° a ±15°.
- Los datos se guardan solo en el celular (almacenamiento del navegador). No borre los datos de navegación de Chrome para ese sitio, o perderá los registros no exportados.
- Mapas base: Esri World Imagery / Topográfico / Calles y OpenStreetMap, con atribución impresa en cada mapa. Google Earth/Google Maps no se usa porque sus condiciones prohíben extraer teselas fuera de su API oficial.

## Opcional: generar un APK
Con la app ya publicada, ingrese su dirección en https://www.pwabuilder.com → *Package for stores* → *Android* para obtener un APK/AAB instalable o publicable en Google Play.
