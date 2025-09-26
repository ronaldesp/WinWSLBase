# Polyglot Cloud POCs Dev Container

Este perfil proporciona un entorno listo para pruebas de concepto multi-cloud en un solo contenedor.

Incluye:
- Python 3.12, .NET 8, PowerShell, Terraform 1.9
- Azure CLI, AWS CLI, Google Cloud SDK
- Node LTS + Azure Functions Core Tools v4
- Extensiones VS Code para Python, C#, PowerShell, Terraform, Azure, AWS, GCP, Docker, YAML/Markdown
- Montaje del socket de Docker del host para usar `docker` dentro del contenedor

Cómo abrir este perfil
- VS Code → Command Palette → "Dev Containers: Open Folder in Container..." → "From `devcontainer.json` in a sub-folder" → selecciona `.devcontainer/polyglot`.
- Alternativamente, abre el repo y usa "Dev Containers: Rebuild and Reopen in Container" y elige el perfil polyglot si se te presenta el selector.

Autenticación (ejecutar dentro del contenedor)
- GitHub: `gh auth login` (y opcional `gh auth setup-git`)
- Azure: `az login` (y si usas Bicep: `az bicep install`)
- AWS: `aws configure sso` (recomendado) o `aws configure`
- GCP: `gcloud auth login` y si necesitas ADC: `gcloud auth application-default login`

Notas
- No incluyas secretos en la imagen ni en `devcontainer.json`.
- Si necesitas Docker, ya puedes usar el CLI gracias al montaje de `/var/run/docker.sock`.