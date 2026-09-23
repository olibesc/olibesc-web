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
- Las páginas legales identifican al titular: no tocar sus datos sin
  confirmación.
- Frontend: taste-skill aplica aquí; ponytail al reescribir o limpiar código.
- Estándar mínimo: `README.md`, `.gitignore`, `.gitattributes` (LF) y este
  `AGENTS.md`.
