---
type: content
title: "Páginas legales y licencia"
description: "Qué cubre cada página legal de olibesc.com (aviso legal, privacidad y cookies), quién figura como titular y por qué el repositorio no tiene licencia de uso."
tags: [legal, privacy, cookies, license]
sources:
  - id: openwiki-source-8037e2358a2c4f9b2c722a11
    resource: repo://AGENTS.md
  - id: openwiki-source-e320da9701799d224f507871
    resource: repo://aviso-legal.html
  - id: openwiki-source-9b664b5ee4667443e3aea97b
    resource: repo://cookies.html
  - id: openwiki-source-db52439eedcdaa2e13646ec1
    resource: repo://privacidad.html
  - id: openwiki-source-23775c3de52f3ab95a13cb8b
    resource: repo://README.md
generated: { by: "claude-code", at: "2026-10-14T15:24:02.349Z" }
verified:
  - by: openwiki/0.6.0
    at: 2026-10-14T15:24:02.349Z
---

# Páginas legales y licencia

El sitio tiene tres páginas legales en HTML estático, en la raíz del
repositorio. La portada enlaza a las tres desde el pie.

## Titular

Las tres páginas identifican al titular del sitio como **Ángel Oliván
(Olibesc)**, con domicilio en Pinseque (Zaragoza) y contacto en
`info@olibesc.com`. Estos datos no se cambian sin confirmación del propio
titular: es una regla del repositorio.

## Qué cubre cada página

| Página | Contenido |
|---|---|
| `aviso-legal.html` | Datos del titular, propiedad intelectual, condiciones de uso, carácter informativo de los contenidos (los datos estadísticos son agregados y anónimos), exención de responsabilidad, enlaces, ley aplicable y jurisdicción, modificaciones y contacto. |
| `privacidad.html` | Responsable del tratamiento, datos que se recogen, finalidades, base legal, plazos de conservación, proveedores con los que se comparten datos, derechos del interesado, seguridad, cookies, cambios y contacto. |
| `cookies.html` | Qué son las cookies, inventario de lo que el sitio guarda en el navegador (ninguna cookie; solo la preferencia de tema `olibesc-theme`, si se elige), las que no usa, servicios de terceros que carga la página (Google Fonts, Cloudflare, GitHub Pages), cómo borrarlo, actualizaciones y contacto. |

Los textos describen lo que la web hace de verdad. Desde el 2026-10-13 la web
es solo informativa: **no tiene formularios ni recoge datos** al navegar, no hay
cookies y la lista de proveedores es la real. La privacidad explica además que
las revisiones de dominio se conservan como máximo 12 meses, que las copias de
seguridad cifradas (R2, jurisdicción UE) pueden guardarlas hasta 90 días más y
que Telegram es la mensajería interna con la que se lanzan. Quedan pendientes el
CIF/NIF del titular, servir las tipografías desde la propia web en vez de
Google Fonts y una revisión profesional de las bases legales (ver el README).

Las condiciones de uso del aviso legal prohíben el uso masivo o automatizado
del sitio y su uso con fines ilícitos.

## Mantener los textos al día

Los textos legales describen lo que hace la web, así que dependen del código:
si la web volviera a recibir datos (un formulario, analítica) o cambiara lo que
guarda el navegador, hay que revisar `privacidad.html` y `cookies.html` en el
mismo cambio. Lo mismo vale para la conservación: la promesa de 12 meses en la
política de privacidad depende de la purga de Postgres y de la regla de borrado
de las copias, que viven en otros repositorios.

## Licencia

El repositorio es público pero **no concede ninguna licencia de uso**: no hay
fichero `LICENSE` y el README declara todos los derechos reservados. Es
coherente con el apartado de propiedad intelectual del aviso legal, que
reserva al titular los textos, imágenes, logotipos, código fuente y diseño del
sitio. No debe añadirse una licencia abierta (MIT u otra).
