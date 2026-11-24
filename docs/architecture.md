# Arquitectura · Aurix

## Aplicación nativa

Aurix está escrita en Kotlin con Jetpack Compose y un sistema de diseño propio, sin Material 3. La lógica que no depende de Android se prueba en la JVM con pruebas automáticas.

## Motor del editor

El editor usa sora-editor, que dibuja solo las líneas visibles, con un coloreado de sintaxis propio que se recalcula línea a línea. Con un archivo de 40 000 líneas y el teclado abierto se midió una mediana de 18 ms por fotograma en un emulador x86_64; en un teléfono real el resultado puede ser distinto.

## Terminal

La terminal usa un PTY nativo y un emulador ANSI propio, con hasta 8 pestañas y un servicio en primer plano para mantener sesiones activas en segundo plano. Incluye un entorno Linux opcional (Alpine ejecutado con proot) y un sistema base propio, compilado desde las fuentes para Aurix, que se está integrando.

## Git

Git funciona con JGit, sin depender de un binario externo: clonar, ramas, fusión, stash, diferencias y un resolutor visual de conflictos bloque a bloque. El inicio de sesión de GitHub permite usar repositorios privados.

## Archivos visibles para otras aplicaciones

Aurix publica su carpeta «Aurix Linux» en el selector de archivos del sistema, de modo que otras aplicaciones, como los gestores de archivos, puedan acceder a ella.

## Ayudas de código

Aurix incluye autocompletado, diagnósticos locales (por ejemplo, paréntesis o comentarios sin cerrar), esquema de símbolos, plegado de bloques y un cliente LSP para conectar servidores de lenguaje que instales dentro de Linux. El cliente LSP es una función reciente y su resultado depende de cada servidor.
