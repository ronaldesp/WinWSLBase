# 05 – Dev Containers: entorno reproducible

## Requisitos

- Docker Desktop con WSL2 (integración habilitada para tu distro).
- Extensión Dev Containers.

## Estructura mínima

```
.devcontainer/
  devcontainer.json
  Dockerfile (opcional)
```

## Plantilla básica incluida en este repo

Consulta `.devcontainer/devcontainer.json` y ajústalo. Incluye:

- Base `mcr.microsoft.com/devcontainers/base:ubuntu`
- Features: git, GitHub CLI
- Extensiones recomendadas para Markdown y YAML

## Uso

- Abre el repo en VS Code → “Dev Containers: Reopen in Container”.
- `gh auth login` dentro del contenedor si usarás HTTPS+PAT, o comparte tu agente SSH.

## Consejos

- Evita guardar tokens dentro de la imagen.
- Usa mounts/volúmenes para caches y `~/.gitconfig` si te conviene.

Siguiente: 06 – Docker.
