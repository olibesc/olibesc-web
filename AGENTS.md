# AGENTS.md

Normas para cualquier agente (Claude Code u otro) que trabaje en este repo.

- **Repo PÚBLICO y web en producción:** cada push a `main` se publica en
  olibesc.com en un par de minutos. Nada de push sin confirmación de Lito.
- Nunca aquí: secretos, datos de clientes ni detalles de la infraestructura
  interna.
- HTML estático sin build. Probar en local (`python -m http.server 8765`)
  antes de proponer cambios.
- Los emails los ofusca Cloudflare al servir la página: el `mailto:` en claro
  del fuente es correcto.
- Las páginas legales identifican al titular (Ángel Oliván): no tocar sus
  datos sin confirmación.
- Frontend: taste-skill aplica aquí; ponytail al reescribir o limpiar código.
- Estándar mínimo: `README.md`, `.gitignore`, `.gitattributes` (LF) y este
  `AGENTS.md`.
- **Sin `LICENSE`, a propósito:** todos los derechos reservados, coherente con
  el aviso legal. No añadir MIT ni ninguna otra licencia.
- Esta es la única copia de la portada: el formulario habla con el workflow
  de auditoría de dominio de n8n, pero la página vive solo aquí.
- Diagrama: `docs/arquitectura.json` → `docs/arquitectura.html` con archify.
- `_config.yml` excluye de la web `docs/` y los `.md` del repo: si se añade un
  fichero que no debe publicarse, añadirlo ahí.
- Wiki en `openwiki/`, generada con openwiki desde Claude Code (no se publica
  en la web). **No hay workflow programado**, aunque el bloque de OpenWiki de
  abajo lo mencione: `.github/workflows/openwiki-update.yml` se ignora porque
  enviaría el código a OpenAI. Para actualizarla, pedir a Claude Code
  «actualiza la wiki de este repo».

<!-- OPENWIKI:START -->

## OpenWiki

This repository has a generated `openwiki/` evidence index. It is optional just-in-time context, not required startup reading.

- Do not enumerate, preload, or search wikis at task start. Use retrieval when the user asks for it, when unfamiliar architecture or dependency behavior materially affects the task, or when source inspection leaves an important uncertainty. Stop once the question is grounded.
- When those conditions apply and OpenWiki retrieval tools are available, use `openwiki_search` for just-in-time context and `openwiki_read` for the relevant complete sections. If search returns `workspace_required`, ask which listed workspace to use and retry with its ID.
- Use `openwiki_list_workspaces` or `openwiki_list_wikis` when workspace membership itself needs to be discovered.
- If the retrieval tools are unavailable, read `openwiki/quickstart.md` and follow its links to the relevant pages.
- Treat source code and tests as authoritative. A brief's unknowns and review items are verification gaps, not automatic requirements.
- Prefer the narrowest quiet validation that proves the changed behavior. Preserve complete failure output.

The scheduled OpenWiki GitHub Actions workflow refreshes the repository wiki. Do not hand-edit generated OpenWiki pages unless explicitly asked; prefer updating source code/docs and letting OpenWiki regenerate.

<!-- OPENWIKI:END -->
