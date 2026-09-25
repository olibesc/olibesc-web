---
type: quickstart
title: "Guía rápida de olibesc-web"
description: "Punto de entrada a la wiki de olibesc-web: qué es el repositorio, cómo ver la web en local, cómo se publica y qué página consultar para cada tarea."
tags: [quickstart, static-site, landing-page]
verified:
  - by: openwiki/0.6.0
    at: 2026-09-25T11:01:50.364Z
sources:
  - id: openwiki-source-96432c8187f1a2124a5afef3
    resource: repo://_config.yml
  - id: openwiki-source-8037e2358a2c4f9b2c722a11
    resource: repo://AGENTS.md
  - id: openwiki-source-f8d10828394c4129061d5b0e
    resource: repo://index.html
  - id: openwiki-source-23775c3de52f3ab95a13cb8b
    resource: repo://README.md
generated: { by: "claude-code", at: "2026-09-25T11:01:50.364Z" }
---

# Guía rápida de olibesc-web

`olibesc-web` es la web pública de Olibesc, [olibesc.com](https://olibesc.com):
cuatro páginas HTML estáticas (portada, aviso legal, privacidad y cookies) y el
logo. No hay build ni dependencias.

## Lo esencial en 30 segundos

- **Ver en local:** `python -m http.server 8765` desde la raíz y abrir
  `http://localhost:8765`.
- **Publicar:** push a `main`. Es un despliegue a producción inmediato, así
  que se prueba antes en local.
- **No publicar un fichero:** añadirlo a `exclude` en `_config.yml`.
- **Sin licencia:** todos los derechos reservados; no añadir `LICENSE`.

## ¿Qué quieres hacer?

| Tarea | Página |
|---|---|
| Entender cómo se sirve la web, qué se publica y qué no | [Publicación: GitHub Pages, dominio y exclusiones](arquitectura/publicacion.md) |
| Tocar la comprobación gratuita de la portada, sus textos o el formato de respuesta | [Flujo de la comprobación de dominio](flujos/comprobacion-de-dominio.md) |
| Revisar o actualizar aviso legal, privacidad o cookies | [Páginas legales y licencia](contenido/paginas-legales.md) |

## Mapa del repositorio

| Ruta | Qué es |
|---|---|
| `index.html` | Portada con la comprobación de SPF, DKIM y DMARC |
| `aviso-legal.html`, `privacidad.html`, `cookies.html` | Páginas legales |
| `logo.png`, `CNAME` | Logo y dominio de GitHub Pages |
| `_config.yml` | Lista de ficheros que no se publican |
| `docs/` | Diagrama de arquitectura (no se publica) |
| `openwiki/` | Esta wiki (no se publica) |
