# 03 – WSL Ubuntu: preparación del entorno

## Actualizar e instalar paquetes básicos

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y build-essential curl git ca-certificates gnupg unzip zip
```

## Configurar Git (WSL)

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu@correo.com"
git config --global core.autocrlf input
```

### HTTPS con PAT usando GitHub CLI

```bash
sudo apt install -y gh
gh auth login
gh auth setup-git
```

### SSH (opción alternativa)

```bash
ssh-keygen -t ed25519 -C "tu@correo.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
cat ~/.ssh/id_ed25519.pub
```

Añade la clave en GitHub → Settings → SSH and GPG keys.

## Docker CLI dentro de WSL

Si Docker Desktop tiene integración WSL, `docker version` debe funcionar dentro de WSL.

Siguiente: 04 – Git + GitHub.
