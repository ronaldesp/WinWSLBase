# 02 – Visual Studio Code: configuración esencial

## Extensiones recomendadas

- WSL (ms-vscode-remote.remote-wsl)
- Dev Containers (ms-vscode-remote.remote-containers)
- Docker (ms-azuretools.vscode-docker)
- GitHub Pull Requests and Issues (GitHub.vscode-pull-request-github)
- GitHub Actions (github.vscode-github-actions) (opcional)
- Markdown All in One (yzhang.markdown-all-in-one)
- YAML (redhat.vscode-yaml)
- EditorConfig (EditorConfig.EditorConfig)

## Configuraciones útiles

En Settings UI o `settings.json`:

```jsonc
{
  // Terminal integrada use WSL Ubuntu por defecto (Windows)
  "terminal.integrated.defaultProfile.windows": "Ubuntu (WSL)",
  // Formato de fin de línea coherente
  "files.eol": "\n",
  // Recomendaciones de extensión
  "extensions.ignoreRecommendations": false
}
```

## Abrir carpetas en WSL o Contenedor

- WSL: Command Palette → “WSL: Reopen Folder in WSL” (o desde WSL: `code .`).
- Dev Container: Command Palette → “Dev Containers: Reopen in Container”.

Siguiente: 03 – WSL.
