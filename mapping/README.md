# MiniMapper

Video mapping básico en un solo archivo HTML. Capas de video/imagen/grilla/color,
cada una con 4 esquinas arrastrables (warp con perspectiva real vía `matrix3d`).

## Uso

1. Abrir `index.html` en Chrome (o Edge).
2. Llevar la ventana a la pantalla del proyector y apretar `F` (o F11) para fullscreen.
3. Arrastrar un video (MP4/WebM) a la ventana → aparece como capa.
4. Arrastrar las 4 esquinas hasta que calce sobre el objeto. La capa **Grilla**
   sirve para calibrar antes de poner contenido real.
5. `Tab` → modo proyección (se oculta todo el UI y el cursor).

## Atajos

| Tecla | Acción |
|---|---|
| `Tab` | alternar edición / proyección |
| `F` | fullscreen |
| Rueda | escalar la capa seleccionada (mantiene proporción) |
| `Shift`+Rueda | rotar la capa seleccionada |
| Flechas | ajuste fino de la esquina activa, o de toda la capa (Shift = ×10) |
| `Espacio` | play/pausa de todos los videos |
| `R` | resetear esquinas de la capa seleccionada |
| `Supr` | borrar capa seleccionada |
| `Esc` | deseleccionar |

## Notas

- Cada video entra con su proporción real, y mover / escalar (rueda) / rotar
  (Shift+rueda) nunca lo deforman. Arrastrar una esquina sí lo deforma: eso es
  a propósito, sirve para compensar el ángulo del proyector contra el objeto.
  `R` vuelve a la proporción original.
- Los videos quedan en loop automáticamente.
- El proyecto (capas, esquinas, opacidades) se guarda solo en el navegador:
  al reabrir la página sigue todo donde estaba, incluidos los archivos
  (se guardan en IndexedDB).
- Si un video bajado de internet no se reproduce, convertirlo a MP4 H.264,
  por ejemplo: `ffmpeg -i entrada.ext -c:v libx264 -pix_fmt yuv420p salida.mp4`.