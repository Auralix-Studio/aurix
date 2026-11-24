# Aurix
Web pública, documentación y política de privacidad de Aurix, el editor de código para Android de Auralix Studio.

Sitio: https://auralix-studio.github.io/aurix/
Política de privacidad: https://auralix-studio.github.io/aurix/privacy.html (en español y en inglés, en la misma página)
Publicaciones: https://github.com/Auralix-Studio/aurix/releases

## Estructura
- index.html: presentación del producto con su identidad visual.
- downloads.html: cómo conseguir Aurix. Aún no está en Google Play; si hay una release estable, aparece aquí.
- docs.html: índice de guías.
- install.html, architecture.html, faq.html, troubleshoot.html: instalación, funcionamiento y ayuda.
- about.html, privacy.html, license.html: información del proyecto, política de privacidad y licencias de terceros.
- changelog.html: historial de releases estables consultado desde GitHub.
- docs/: documentación en Markdown.
- assets/: recursos gráficos locales.
- PRIVACY.md, CHANGELOG.md, LICENSE: referencias del repositorio.

## Desarrollo
Sitio estático sin dependencias ni build obligatorio. Servir esta carpeta con un servidor HTTP. Los enlaces son relativos y funcionan bajo /aurix/ en GitHub Pages.

Las páginas HTML se generan desde `Webs/build-sites.cjs` con el contenido de `Webs/aurix.config.cjs` (`node build-sites.cjs aurix`). Para cambiar un texto, edita ese archivo y vuelve a generar; no edites los HTML a mano. `style.css`, `app.js` y `ui.js` sí se editan directamente.

La consulta de releases no utiliza tokens. Los fallos de red y la ausencia de publicaciones muestran un aviso; no se inventan versiones ni enlaces a binarios inexistentes.

## Publicación
GitHub Pages usa `.github/workflows/pages.yml` al actualizar main, publicar una release estable o ejecutarlo manualmente. Configurar Pages con origen GitHub Actions. `scripts/prepare_site.py` prepara solo los archivos públicos en `_site` y, si existe una release estable con `version.json`, verifica su identidad (paquete `pro.auralix.aurix`), tag, archivos, tamaños y hashes antes de desplegar.

Pruebas: `python -m unittest discover -s scripts -p 'test_*.py'`. Desde la carpeta superior Webs, `node test-sites.cjs` valida los clientes web.

El código de la app se mantiene en otro repositorio (privado). Nunca copiar su historial ni sus carpetas a este repositorio.

## Qué debe seguir siendo cierto
La web describe el estado real de la app. Si cambia lo que la app hace con los datos (servidores, analítica, anuncios, permisos nuevos), hay que actualizar la política de privacidad aquí y la declaración de «Seguridad de los datos» en Play Console.
