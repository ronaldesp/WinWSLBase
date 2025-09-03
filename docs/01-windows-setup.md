# 01 – Windows 11: requisitos e instalación base

Objetivo: dejar Windows 11 listo para desarrollo con WSL2.

## Requisitos

- Windows 11 actualizado (Windows Update).
- Cuenta con permisos de administrador.

## Habilitar WSL2 y plataforma de máquina virtual

PowerShell (Admin):

```powershell
wsl --install
# Si ya tienes WSL, asegúrate de:
wsl --set-default-version 2
```

Reinicia si es requerido. Instala Ubuntu cuando se te solicite o desde Microsoft Store (Ubuntu LTS recomendada).

## Instalar VS Code

- Descarga desde https://code.visualstudio.com/ y completa la instalación.

## Instalar Windows Terminal (opcional, recomendado)

- Microsoft Store: “Windows Terminal”. Configura un perfil para Ubuntu (WSL).

## Instalar Git for Windows (si trabajarás también en Windows)

- https://git-scm.com/download/win
- Configura line endings: Checkout Windows-style, commit Unix-style (recomendado para repos multiplataforma).

## Instalar Docker Desktop con WSL2

- https://www.docker.com/products/docker-desktop/
- Settings → General: Enable the WSL 2 based engine
- Settings → Resources → WSL Integration: habilita tu distro Ubuntu.

Siguiente: 02 – VS Code.
