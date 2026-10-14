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

## Qué promete la portada (y de dónde sale)

Lo que la web dice tiene que existir en otro sitio. Revisado el 2026-10-14:

| Promesa de la portada | Respaldo | Estado |
|---|---|---|
| Tarjeta «Correo profesional y revisado» (de Gmail/Yahoo a dominio propio) | `olibesc-comercial/docs/producto-entrada.md` | **Hipótesis en prueba**: sin precio ni alcance cerrados |
| Cuota «más barata con 3 meses de permanencia, o sin ella» | mismo documento y plantilla del informe de `olibesc-n8n` | Fijar los importes antes de publicar cifras |
| «Protección del dominio sin cortes» | `olibesc-piloto-soc/docs/TARIFARIO.md` (Nivel 1) y el catálogo de remediación | Real |
| Tarjeta «Vigilancia continua del correo» | Nivel 1 del tarifario, integración por API con Microsoft 365 / Google Workspace | **Próximamente**: sin medir ni desplegar |
| «63 %» y barras (139 empresas) | `_clientes/hub-aragon-defensa/hub_aragon_defensa_leads.csv`, análisis de julio de 2026: 46 sin DMARC, 42 en `p=none` o `reject` con `pct=0`, 42 en cuarentena, 9 en `reject` | Real. El CSV no se publica |

No añadir a la portada un servicio que no figure en esa tabla ni en los
documentos de `olibesc-comercial` o `olibesc-piloto-soc`.

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
