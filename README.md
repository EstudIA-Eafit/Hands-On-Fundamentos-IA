# Laboratorios · Fundamentos de IA

Laboratorios web interactivos del curso. Cada alumno los recorre desde su propio dispositivo, con Gemini o ChatGPT abiertos en otra pestaña.

Es un sitio estático, sin frameworks, sin build y sin backend. No se conecta a ninguna IA. Las respuestas se guardan solo en el navegador de cada alumno (`localStorage`).

## Estructura

```
index.html                    Página de inicio con el menú de laboratorios
sesion-1/index.html           Laboratorio 1: Pide bien y verifica (4 pasos, 50 min)
.github/workflows/pages.yml   Despliegue automático en GitHub Pages
```

Cada laboratorio es un solo archivo, con su HTML, CSS y JavaScript propios.

## Publicar en GitHub Pages

El despliegue lo hace GitHub Actions con el flujo `.github/workflows/pages.yml`.

1. Solo la primera vez: en GitHub, abre el repositorio, entra a **Settings > Pages** y en **Build and deployment** elige **Source: GitHub Actions**.
2. Sube los archivos a la rama `main`:
   ```
   git add index.html sesion-1 README.md .github
   git commit -m "Laboratorios del curso"
   git push origin main
   ```
3. Abre la pestaña **Actions** y espera a que termine "Publicar en GitHub Pages" (uno o dos minutos). La dirección queda en el resumen de la ejecución y en **Settings > Pages**, con la forma `https://usuario.github.io/repositorio/`.

El flujo publica todo el repositorio menos los archivos y carpetas ocultos (los que empiezan por punto) y este README. También se puede lanzar a mano desde **Actions > Publicar en GitHub Pages > Run workflow**.

Direcciones para compartir (un código QR en la primera diapositiva funciona bien):

- Menú: `https://usuario.github.io/repositorio/`
- Laboratorio 1, directo: `https://usuario.github.io/repositorio/sesion-1/`

Cada cambio que subas a `main` se publica solo.

## Agregar un laboratorio

1. Crea una carpeta nueva, por ejemplo `sesion-2`, con su propio `index.html`. Lo más fácil es copiar `sesion-1/index.html` y cambiar el contenido.
2. En el laboratorio nuevo, cambia el valor de `CLAVE` (al comienzo del `<script>`) por uno distinto, por ejemplo `laboratorio-ia-sesion-2`. Si dos laboratorios comparten la clave, se pisan las respuestas.
3. En el `index.html` de la raíz, copia el bloque `<li class="lab">` y ajusta la sesión, el título, la descripción, el enlace y `data-clave` (la misma clave del paso 2). El archivo tiene un comentario que marca el lugar.

## Probar antes de la clase

Abre `index.html` con doble clic o entra a la dirección publicada. Enlaces directos a los pasos del laboratorio 1: `sesion-1/index.html#preparar`, `#caso-guiado`, `#tu-caso`, `#resumen`.

Para empezar de cero en un dispositivo, usa el enlace "Borrar mis respuestas" al final del laboratorio.

## Cambiar el contenido del laboratorio 1

Todo está en `sesion-1/index.html`. Las frases del caso guiado, los errores, las ideas de arranque y las sugerencias de criterios están al comienzo del bloque `<script>`, en las listas `FRASES`, `IDEAS` y `SUGERENCIAS`. Los colores están al comienzo del bloque `<style>`, en `:root` (tema claro) y en `@media (prefers-color-scheme: dark)` (tema oscuro). La página de inicio usa los mismos colores; si los cambias, cámbialos en los dos archivos.
