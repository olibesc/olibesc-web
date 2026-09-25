---
type: architecture
title: "Publicación: GitHub Pages, dominio y exclusiones"
description: "Cómo se sirve olibesc.com: HTML estático sin paso de build publicado por GitHub Pages con dominio propio y Cloudflare delante, qué ficheros del repo se excluyen de la web y cómo previsualizar cambios."
tags: [deployment, github-pages, static-site, cloudflare]
verified:
  - by: openwiki/0.6.0
    at: 2026-09-25T11:01:50.364Z
sources:
  - id: openwiki-source-96432c8187f1a2124a5afef3
    resource: repo://_config.yml
  - id: openwiki-source-8037e2358a2c4f9b2c722a11
    resource: repo://AGENTS.md
  - id: openwiki-source-4d323772649941a55df7f8cd
    resource: repo://CNAME
  - id: openwiki-source-f8d10828394c4129061d5b0e
    resource: repo://index.html
  - id: openwiki-source-23775c3de52f3ab95a13cb8b
    resource: repo://README.md
generated: { by: "claude-code", at: "2026-09-25T11:01:50.364Z" }
---

# Publicación: GitHub Pages, dominio y exclusiones

`olibesc-web` es la web pública de Olibesc. No hay aplicación ni paso de
compilación: el repositorio **es** el sitio. Cada fichero HTML se sirve tal
cual está en la rama `main`.

## Cómo llega una página al visitante

1. Se hace push a `main`. GitHub Pages publica la rama en un par de minutos
   ([README.md](../../README.md), sección «Uso»).
2. El dominio del sitio lo fija el fichero `CNAME`, que contiene solo
   `olibesc.com`.
3. Por delante de GitHub Pages está Cloudflare, que sirve el sitio por HTTPS.
   Cloudflare reescribe al vuelo los enlaces `mailto:`: por eso en el HTML
   fuente las direcciones de correo aparecen en claro y en el navegador salen
   ofuscadas. El fuente es correcto así y no hay que «arreglarlo».

No hay dependencias que instalar. Para ver la web en local basta un servidor
estático desde la raíz del repositorio:

```bash
python -m http.server 8765
# http://localhost:8765
```

## Qué se publica y qué no

GitHub Pages publica **todo** el repositorio salvo lo que se excluye en
`_config.yml`. Ahí se excluyen los documentos internos del repositorio, que no
forman parte de olibesc.com:

| Excluido | Qué es |
|---|---|
| `README.md`, `AGENTS.md`, `CLAUDE.md` | Documentación del repositorio y normas para agentes |
| `docs/` | Diagrama de arquitectura generado con archify |
| `openwiki/` | Esta wiki |

**Regla práctica:** cualquier fichero nuevo que no deba verse en la web tiene
que añadirse a la lista `exclude` de `_config.yml` en el mismo cambio. Sin esa
entrada, el siguiente push lo publica.

## Recursos externos que carga el sitio

Las páginas son autocontenidas (estilos y scripts en línea), con una excepción:
las tipografías (Syne y DM Sans) se cargan desde Google Fonts
(`fonts.googleapis.com` y `fonts.gstatic.com`). Además, la portada llama al
webhook de auditoría cuando el visitante lanza una comprobación (ver
[Flujo de la comprobación de dominio](../flujos/comprobacion-de-dominio.md)).

## Convenciones del repositorio

- `.gitattributes` fuerza finales de línea LF en todos los ficheros de texto.
- `.gitignore` ignora ficheros de sistema y editores, y las capturas que genera
  la verificación visual de archify (`docs/*.visual-check.*`).
- El repositorio **no tiene fichero `LICENSE` a propósito**: el contenido tiene
  todos los derechos reservados (ver
  [Páginas legales y licencia](../contenido/paginas-legales.md)).
- Cada push a `main` es un despliegue a producción, por lo que los cambios se
  prueban antes en local.
