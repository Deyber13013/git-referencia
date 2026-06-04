# 📘 Mi Referencia de Git

> Guía personal de comandos Git para consultar cuando la necesite.
> Los comandos Git son iguales en cualquier terminal (PowerShell, CMD, bash).

## Índices

- [Flujo de trabajo diario](#flujo-de-trabajo-diario)
- [Comandos consultivos](#comandos-consultivos)
- [Comandos procedimentales](#comandos-procedimentales)
- [Trabajar con GitHub (remoto)](#trabajar-con-github-remoto)
- [Deshacer cambios](#deshacer-cambios)

---

## Flujo de trabajo diario

El orden mental de cada cambio:

```
Editar + Ctrl+S → git status → git diff → git add → git commit → git push
   (VS Code)        (¿qué?)     (detalle)  (preparar) (guardar)   (subir)
```

| Paso | Comando                   | Qué hace                                       |
| ---- | ------------------------- | ---------------------------------------------- |
| 1    | `git status`              | Ver qué archivos cambiaron                     |
| 2    | `git diff`                | Ver el detalle línea por línea (salir con `q`) |
| 3    | `git add archivo.md`      | Preparar un archivo específico                 |
| 4    | `git commit -m "mensaje"` | Guardar la versión                             |
| 5    | `git push`                | Subir los commits al remoto                    |

> **Regla:** `add` prepara · `commit` guarda · `push` sube.

---

## Comandos consultivos

> 🔍 Solo leen información. No cambian nada, son 100% seguros.

| Comando             | Qué responde                         |
| ------------------- | ------------------------------------ |
| `git status`        | ¿Qué cambió y qué está preparado?    |
| `git diff`          | ¿Qué líneas cambié (sin preparar)?   |
| `git diff --staged` | ¿Qué voy a commitear (ya preparado)? |
| `git log --oneline` | Historial compacto de commits        |
| `git remote -v`     | ¿A qué remoto está conectado?        |
| `git branch`        | ¿En qué rama estoy?                  |

---

## Comandos procedimentales

> ⚙️ Cambian el estado del repositorio.

```bash
git init                    # Inicializa el repo (una vez por proyecto)
git add archivo.md          # Prepara un archivo específico
git add .                   # Prepara TODOS los cambios de la carpeta actual
git commit -m "mensaje"     # Guarda la versión preparada
```

---

## Trabajar con GitHub (remoto)

```bash
git remote add origin https://github.com/USUARIO/REPO.git   # Vincular (una vez)
git push -u origin main     # Primer push (-u recuerda la conexión)
git push                    # Pushes siguientes
git pull                    # Traer e integrar cambios remotos
git fetch                   # Descargar sin integrar (inspeccionar primero)
```

---

## Eliminar cambios

> ⚠️ Usar con cuidado. Verificar siempre con `git status` antes.

```bash
git restore archivo.md            # Descarta cambios NO preparados
git restore --staged archivo.md   # Quita del área de preparado (sin borrar el cambio)
git commit --amend -m "Nuevo"     # Corrige el mensaje del último commit (si no lo subiste)
```

**Nunca** reescribas historia (`amend`, `reset`) sobre commits que ya hiciste `push`.
