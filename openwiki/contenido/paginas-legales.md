---
type: content
title: "Páginas legales y licencia"
description: "Qué cubre cada página legal de olibesc.com (aviso legal, privacidad y cookies), quién figura como titular y por qué el repositorio no tiene licencia de uso."
tags: [legal, privacy, cookies, license]
verified:
  - by: openwiki/0.6.0
    at: 2026-09-25T11:01:50.364Z
sources:
  - id: openwiki-source-8037e2358a2c4f9b2c722a11
    resource: repo://AGENTS.md
  - id: openwiki-source-e320da9701799d224f507871
    resource: repo://aviso-legal.html
  - id: openwiki-source-db52439eedcdaa2e13646ec1
    resource: repo://privacidad.html
  - id: openwiki-source-23775c3de52f3ab95a13cb8b
    resource: repo://README.md
generated: { by: "claude-code", at: "2026-09-25T11:01:50.364Z" }
---

# Páginas legales y licencia

El sitio tiene tres páginas legales en HTML estático, en la raíz del
repositorio. La portada enlaza a la privacidad y al aviso legal desde el pie;
la política de privacidad enlaza a su vez a la de cookies.

## Titular

Las tres páginas identifican al titular del sitio como **Ángel Oliván
(Olibesc)**, con domicilio en Pinseque (Zaragoza) y contacto en
`info@olibesc.com`. Estos datos no se cambian sin confirmación del propio
titular: es una regla del repositorio.

## Qué cubre cada página

| Página | Contenido |
|---|---|
| `aviso-legal.html` | Datos del titular, propiedad intelectual, condiciones de uso, descripción del servicio de auditoría gratuita y su limitación de responsabilidad, enlaces, ley aplicable y jurisdicción, modificaciones y contacto. |
| `privacidad.html` | Responsable del tratamiento, datos que se recogen, finalidades, base legal, plazos de conservación, proveedores con los que se comparten datos, derechos del interesado, seguridad, cookies, cambios y contacto. |
| `cookies.html` | Qué son las cookies, inventario de las que declara el sitio, las que no usa, servicios de terceros, cómo gestionarlas, actualizaciones y contacto. |

El aviso legal fija dos reglas de uso relevantes para la herramienta de la
portada: prohíbe analizar dominios de los que no se sea titular o para los que
no se tenga autorización, y prohíbe el uso masivo o automatizado del
formulario.

## Mantener los textos al día

Los textos legales describen lo que hace la web, así que dependen del código:
si cambia lo que envía el formulario, adónde van los datos o qué guarda el
navegador, hay que revisar `privacidad.html` y `cookies.html` en el mismo
cambio. El comportamiento real del formulario está descrito en
[Flujo de la comprobación de dominio](../flujos/comprobacion-de-dominio.md).

## Licencia

El repositorio es público pero **no concede ninguna licencia de uso**: no hay
fichero `LICENSE` y el README declara todos los derechos reservados. Es
coherente con el apartado de propiedad intelectual del aviso legal, que
reserva al titular los textos, imágenes, logotipos, código fuente y diseño del
sitio. No debe añadirse una licencia abierta (MIT u otra).
