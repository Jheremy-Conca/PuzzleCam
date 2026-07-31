# PuzzleCam — Gesture Capture
**© 2026 aiwithunnati — all rights reserved**

Un fotomatón-rompecabezas controlado con gestos de mano, que corre enteramente en el navegador. Sin instalación, sin backend, sin frameworks. Solo tus manos y una webcam.

---

## ¿Qué es esto?

Usas tus manos como marco de cámara, haces pinza para tomar una foto, resuelves un rompecabezas con los dedos, y ves cómo estalla en una tira de fotos estilo Polaroid. Todo corre en una sola pestaña del navegador, sin configuración previa.

Construido con JavaScript puro, seguimiento de manos con MediaPipe y la Web Audio API. Sin React. Sin npm. Nada que instalar.

---

## Estructura del proyecto

```
puzzlecam/
├── index.html      # estructura de la interfaz (stage, HUD, galería, modal de tira)
├── app.js           # lógica completa: tracking, puzzle, shatter, audio, grabación
├── css/
│   └── styles.css   # estética del stage y la galería lateral
├── guide.html        # landing page de presentación/tutorial del proyecto
└── README.md
```

> Nota: `index.html` referencia la hoja de estilos como `css/styles.css` — asegúrate de que `styles.css` esté dentro de una carpeta `css/` (o ajusta la ruta en el `<link>` si prefieres tenerlo en la raíz).

---

## Cómo correrlo

**1. Clona el repositorio**
```bash
git clone (https://github.com/Jheremy-Conca/PuzzleCam.git)
cd puzzlecam
```

**2. Ábrelo en VS Code y usa Go Live**

Instala la extensión [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) de Ritwick Dey si no la tienes. Luego haz clic en **Go Live** en la esquina inferior derecha.

**3. Ábrelo en Chrome o Edge**
```
http://localhost:5500
```
Permite el acceso a la cámara cuando el navegador lo solicite.

> Necesita internet la primera vez para descargar el modelo de manos de MediaPipe (~10MB). Después de eso funciona sin conexión.

---

## Cómo jugar

| gesto | qué hace |
|---|---|
| levantar ambas manos | la cámara empieza a rastrear tus manos |
| pinza con ambas manos | define el marco de la foto y arranca la cuenta regresiva de 3 segundos |
| pinza con una mano sobre una pieza | arrastra esa pieza del rompecabezas |
| soltar la pieza cerca del lugar correcto | encaja automáticamente |
| puño cerrado (sostenido) | guarda el rompecabezas completado / reinicia el tablero |

**El flujo completo:**
1. levanta ambas manos — el espacio entre tus dedos índice se convierte en el marco de tu cámara
2. haz pinza con ambas manos → cuenta regresiva de 3 segundos → flash → foto capturada en blanco y negro
3. resuelve el rompecabezas 3x3 arrastrando piezas con gesto de pinza
4. cierra el puño al terminar → las piezas estallan → se guarda como una polaroid a color con fecha y número de foto
5. completa 3 rompecabezas → aparece tu tira de fotos completa → descárgala

---

## Qué lo hace diferente

- los rompecabezas están **en blanco y negro mientras se resuelven**, luego se revelan **a color** al guardarse
- **flash de cámara** en el momento de la captura
- **bordes de polaroid** con fecha y número estampados en cada foto
- **diseño de sonido** — beeps de cuenta regresiva, snap de piezas, estallido del shatter, tono de finalización
- **grabación de video** de cada resolución, descargable como WebM
- **ventana emergente de tira de fotos** dentro del juego al completar las 3
- efecto de viñeta sutil en cada foto para un look clásico de fotomatón
- cero frameworks, cero dependencias, todo corre en el navegador

---

## Tecnologías usadas

- MediaPipe Tasks Vision `v0.10.14` — detección de landmarks de mano
- Canvas 2D API — renderizado, efectos, rompecabezas, física del shatter
- Web Audio API — todos los sonidos generados en código, sin archivos de audio
- MediaRecorder API — captura de video
- JavaScript puro (ES Modules) — sin frameworks, sin build step

---

## Compatibilidad de navegadores

| navegador | soporte |
|---|---|
| Chrome / Edge | recomendado |
| Firefox | funciona |
| Safari | limitado |
| móvil | no recomendado |

---

## Etiquétame

si lo pruebas me encantaría ver tu tira de fotos. etiqueta **@aiwithunnati** — ¡diviértete!

---

## Licencia

MIT — libre de usar, modificar y compartir.
