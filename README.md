# olibesc-web

Web pública de Olibesc, [olibesc.com](https://olibesc.com): ciberseguridad para
pymes y autónomos. Es HTML estático servido con GitHub Pages, con Cloudflare
por delante.

## Estructura

```
index.html        portada informativa; el contacto es solo por correo (sin formularios)
aviso-legal.html
privacidad.html
cookies.html
logo.png
CNAME             dominio de GitHub Pages
```

## Instalación

No hay dependencias ni paso de build.

## Uso

Para verla en local:

```bash
python -m http.server 8765
# http://localhost:8765
```

Publicar: hacer push a `main`. GitHub Pages la publica en un par de minutos.

## Páginas legales: pendiente

Revisadas el 2026-09-25 para que describan lo que la web hace de verdad (sin
cookies, proveedores reales). Actualizadas el 2026-10-13 al retirar el formulario
de auditoría: la web ya no recoge datos. Falta:

- El **CIF/NIF** del titular en el aviso legal y la política de privacidad.
- **Servir las tipografías desde la propia web** en vez de Google Fonts, para
  que Google no reciba la IP de cada visitante. Cuando se haga, quitar Google
  de la política de cookies y de la de privacidad.
- Una revisión profesional de las bases legales (prospección entre empresas y
  la revisión de dominios vía Telegram, que opera fuera del EEE).

## Arquitectura

Diagrama interactivo en [`docs/arquitectura.html`](docs/arquitectura.html)
(se abre en el navegador). Su fuente es `docs/arquitectura.json`, generado con
archify.

## Licencia

Todos los derechos reservados. El código, los textos y el logo son propiedad
del titular de Olibesc (ver [aviso legal](aviso-legal.html)); que el repo sea
público no concede permiso para reutilizarlos.
