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

## Perfil "Polyglot Cloud POCs"

Para pruebas de concepto multi-cloud (Python, .NET, PowerShell, Terraform, Azure/AWS/GCP y Azure Functions), este repo incluye un perfil adicional de Dev Container en `./.devcontainer/polyglot/`.

Cómo abrirlo:
- VS Code → Command Palette → "Dev Containers: Open Folder in Container..."
- Elige "From `devcontainer.json` in a sub-folder" y selecciona `.devcontainer/polyglot`.

Incluye:
- Python 3.12, .NET 8, PowerShell, Terraform 1.9
- Azure CLI, AWS CLI, Google Cloud SDK
- Node LTS y Azure Functions Core Tools v4 (vía npm)
- Extensiones VS Code para los stacks anteriores
- Montaje del socket de Docker del host (`/var/run/docker.sock`)

Después de abrir el contenedor, autentícate según tu cloud/servicio:
- `gh auth login`
- `az login`
- `aws configure sso` (o `aws configure`)
- `gcloud auth login`

Consejos:
- Mantén versiones fijas en `features` para reproducibilidad.
- Evita secretos en imagen/config; usa logins interactivos.
