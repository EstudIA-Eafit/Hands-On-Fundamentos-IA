# Laboratorios · Fundamentos de IA

Laboratorios web interactivos del curso. Cada alumno los recorre desde su propio dispositivo, con Gemini o ChatGPT abiertos en otra pestaña.

Es un sitio estático, sin frameworks, sin build y sin backend. No se conecta a ninguna IA. Las respuestas se guardan solo en el navegador de cada alumno (`localStorage`).

## Estructura

```
index.html                    Página de inicio con el menú de laboratorios
sesion-1/index.html           Sesión 1: Pide bien y verifica (4 pasos, 50 min)
sesion-2/index.html           Sesión 2: laboratorio individual (30 min) y reto en parejas (40 min)
sesion-3/index.html           Sesión 3: verificar afirmaciones, individual (30 min) y en parejas (40 min)
.github/workflows/pages.yml   Despliegue automático en GitHub Pages
```

Cada laboratorio es un solo archivo, con su HTML, CSS y JavaScript propios.

## Publicar en GitHub Pages

El despliegue lo hace GitHub Actions con el flujo `.github/workflows/pages.yml`.

1. Solo la primera vez: en GitHub, abre el repositorio, entra a **Settings > Pages** y en **Build and deployment** elige **Source: GitHub Actions**.
2. Sube los archivos a la rama `main`:
   ```
   git add index.html sesion-1 sesion-2 README.md .github
   git commit -m "Laboratorios del curso"
   git push origin main
   ```
3. Abre la pestaña **Actions** y espera a que termine "Publicar en GitHub Pages" (uno o dos minutos). La dirección queda en el resumen de la ejecución y en **Settings > Pages**, con la forma `https://usuario.github.io/repositorio/`.

El flujo publica todo el repositorio menos los archivos y carpetas ocultos (los que empiezan por punto) y este README. También se puede lanzar a mano desde **Actions > Publicar en GitHub Pages > Run workflow**.

Direcciones para compartir (un código QR en la primera diapositiva funciona bien):

- Menú: `https://usuario.github.io/repositorio/`
- Sesión 1: `https://usuario.github.io/repositorio/sesion-1/`
- Sesión 2, portada: `https://usuario.github.io/repositorio/sesion-2/`
- Sesión 2, laboratorio individual: `https://usuario.github.io/repositorio/sesion-2/#laboratorio`
- Sesión 2, reto en parejas: `https://usuario.github.io/repositorio/sesion-2/#reto`
- Sesión 3, portada: `https://usuario.github.io/repositorio/sesion-3/`
- Sesión 3, laboratorio 1 (individual): `https://usuario.github.io/repositorio/sesion-3/#laboratorio-1`
- Sesión 3, laboratorio 2 (en parejas): `https://usuario.github.io/repositorio/sesion-3/#laboratorio-2`

Los enlaces `#laboratorio` y `#reto` (sesión 2) y `#laboratorio-1` y `#laboratorio-2` (sesión 3) abren cada parte en el paso donde iba el alumno (o en el primero, si no ha empezado). Para el reto, pega el enlace en el chat de Zoom antes de abrir las salas.

Cada cambio que subas a `main` se publica solo.

## Agregar un laboratorio

1. Crea una carpeta nueva, por ejemplo `sesion-2`, con su propio `index.html`. Lo más fácil es copiar `sesion-1/index.html` y cambiar el contenido.
2. En el laboratorio nuevo, cambia el valor de `CLAVE` (al comienzo del `<script>`) por uno distinto, por ejemplo `laboratorio-ia-sesion-2`. Si dos laboratorios comparten la clave, se pisan las respuestas.
3. En el `index.html` de la raíz, copia el bloque `<li class="lab">` y ajusta la sesión, el título, la descripción, el enlace y `data-clave` (la misma clave del paso 2). El archivo tiene un comentario que marca el lugar.

## Probar antes de la clase

Abre `index.html` con doble clic o entra a la dirección publicada. Enlaces directos a los pasos de la sesión 1: `sesion-1/index.html#preparar`, `#caso-guiado`, `#tu-caso`, `#resumen`. En la sesión 2: `sesion-2/index.html#laboratorio-1` a `#laboratorio-3` y `#reto-1` a `#reto-5`. En la sesión 3: `sesion-3/index.html#laboratorio-1-paso-1` a `#laboratorio-1-paso-3` y `#laboratorio-2-paso-1` a `#laboratorio-2-paso-5`.

Para empezar de cero en un dispositivo, usa el enlace "Borrar mis respuestas" al final del laboratorio.

## Cambiar el contenido de la sesión 3

Todo está en `sesion-3/index.html`, en el objeto `DATOS` al comienzo del bloque `<script>`: el expediente (documentos, apartados, fechas, vigencia y alcance), la pregunta que se copia, la respuesta preparada, la clave de las 11 afirmaciones y los temas del laboratorio 2. Las tarjetas del expediente, el texto que se copia y la clave se arman desde ahí, así que basta con editar un solo lugar.

## Cambiar el contenido de la sesión 2

Todo está en `sesion-2/index.html`. La petición vaga, las cinco partes, la instrucción del reto, los criterios y los tres caminos están al comienzo del bloque `<script>`, en `PETICION_VAGA`, `PARTES`, `INSTRUCCION_RETO`, `CRITERIOS` y `CAMINOS`. El límite de palabras del criterio 1 es `LIMITE`. El contador separa por espacios y saltos de línea, y no cuenta líneas vacías ni signos sueltos (viñetas, guiones o emojis sin letras ni números).

## Cambiar el contenido de la sesión 1

Todo está en `sesion-1/index.html`. Las frases del caso guiado, los errores, las ideas de arranque y las sugerencias de criterios están al comienzo del bloque `<script>`, en las listas `FRASES`, `IDEAS` y `SUGERENCIAS`. Los colores están al comienzo del bloque `<style>`, en `:root` (tema claro) y en `@media (prefers-color-scheme: dark)` (tema oscuro). La página de inicio usa los mismos colores; si los cambias, cámbialos en los dos archivos.
