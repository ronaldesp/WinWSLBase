# 04 – Git + GitHub: autenticación y buenas prácticas

## Elige un método

- HTTPS + PAT (sencillo con GitHub CLI)
- SSH (sin token, con claves)

## HTTPS + PAT con GitHub CLI (recomendado)

```bash
sudo apt install -y gh
gh auth login                 # GitHub.com → HTTPS → Login with a token / browser
gh auth setup-git             # configura helper de Git
gh auth status
```

Verifica remoto y acceso:

```bash
git remote -v
git ls-remote origin -h
```

## SSH

```bash
ssh-keygen -t ed25519 -C "tu@correo.com"
eval "$(ssh-agent -s)"; ssh-add ~/.ssh/id_ed25519
ssh -T git@github.com
git remote set-url origin git@github.com:<user>/<repo>.git
```

## Buenas prácticas

- Usa `core.autocrlf input` en Linux/WSL; `true` en Windows si editas fuera de contenedores.
- Activa 2FA en GitHub.
- Evita tokens en texto plano; usa gh o GCM como credential helper.

### Fin de línea (EOL) y `core.autocrlf`

Por qué: Windows suele usar CRLF, Linux/WSL usa LF. Git debe normalizar a LF dentro del repo para evitar diffs ruidosos. La regla práctica es:

- Linux/WSL: `core.autocrlf = input` (convierte CRLF→LF al hacer commit; no cambia tu working tree al checkout).
- Windows (si editas con editores nativos fuera de contenedores): `core.autocrlf = true` (repo en LF, working tree en CRLF para comodidad de editores Windows).
- Windows (si solo editas dentro de WSL/Dev Containers): puedes dejarlo en `input` o `false` para evitar dobles conversiones.

Configura así:

En Linux/WSL (bash):

```bash
git config --global core.autocrlf input
git config --global --get core.autocrlf
```

En Windows (PowerShell, Git nativo):

```powershell
git config --global core.autocrlf true
git config --global --get core.autocrlf
```

Opcional: refuerza por archivo con `.gitattributes` en la raíz del repo (previene sorpresas en equipos mixtos):

```
* text=auto
*.sh  text eol=lf
*.yml text eol=lf
*.yaml text eol=lf
*.ps1 text eol=crlf
*.bat text eol=crlf
```

Siguiente: 05 – Dev Containers.
