# 06 – Docker Desktop con WSL2 (Ubuntu)

Guía rápida para usar Docker Desktop en Windows con backend WSL2 e integrarlo con tu distro Ubuntu.

## Requisitos previos

- Windows 10/11 con WSL2 y una distro Ubuntu instalada y funcionando.
- Si no lo tienes aún, sigue primero `03-wsl-setup.md`.

## 1) Instalar Docker Desktop (Windows)

Opción A (recomendada, requiere Windows 10 1709+/11 con winget):

```powershell
winget install -e --id Docker.DockerDesktop
```

Opción B: descarga desde la web oficial de Docker Desktop e instálalo manualmente.

Durante la instalación/primer arranque:
- Habilita “Use WSL 2 based engine”.
- No necesitas Hyper-V para este escenario.

## 2) Activar integración con WSL2

En Docker Desktop: Settings → Resources → WSL Integration
- Marca “Enable integration with my default WSL distro”.
- Activa el toggle de tu distro “Ubuntu”.

Aplica los cambios y asegúrate de que Docker Desktop esté corriendo.

## 3) Probar desde Ubuntu (WSL)

Ejecuta dentro de tu terminal WSL (bash):

```bash
# Ver contexto y conexión
docker context ls

# Versión cliente/servidor
docker version

# Probar una imagen simple
docker run --rm hello-world

# Comprobar Compose V2
docker compose version
```

Si todo está OK, verás la salida del contenedor hello-world y versiones de cliente/servidor.

## 4) Ajustes recomendados

- Settings → Resources: asigna CPU/RAM/Swap razonables según tu equipo.
- Settings → General: deja activo “Use Docker Compose V2”.
- Opcional: cambia la ubicación del disco de Docker Desktop si necesitas más espacio.

## 5) Notas importantes

- No instales Docker Engine con apt dentro de Ubuntu cuando uses Docker Desktop. La integración WSL ya te provee el daemon; evita conflictos.
- El socket debe existir en `/var/run/docker.sock` desde WSL cuando Docker Desktop está activo.

## 6) Problemas comunes (resumen)

- “Cannot connect to the Docker daemon”: asegúrate de que Docker Desktop está abierto y que la integración WSL para “Ubuntu” está habilitada. Luego:

```powershell
wsl --shutdown
```

Reabre Docker Desktop y tu terminal WSL.

- “permission denied” o conflictos: si instalaste Docker Engine vía apt, desinstálalo o detén su servicio para evitar chocar con Docker Desktop.

Consulta más detalles en `troubleshooting.md`.

Siguiente: Troubleshooting.
