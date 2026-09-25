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
