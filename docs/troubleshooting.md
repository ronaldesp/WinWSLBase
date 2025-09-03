# Troubleshooting

## WSL no arranca o está lento

- `wsl --status` y `wsl --list --verbose`
- Reinicia servicios LxssManager o sistema.
- Resetea/redimensiona disco si es necesario.

## VS Code usa Git equivocado

- Si abriste carpeta en Windows: usará Git de Windows.
- Reabre en WSL: “WSL: Reopen Folder in WSL” para usar `/usr/bin/git`.
- En contenedor: usa Git del contenedor.

## Docker no funciona desde WSL

- Activa WSL Integration en Docker Desktop para tu distro.
- Verifica `docker context ls` y que `//var/run/docker.sock` esté accesible.

## gh auth problemas

- `gh auth status`
- Repite `gh auth login` y `gh auth setup-git`.
- Para SSH: `ssh -T git@github.com`.
