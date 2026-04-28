# Apuntes_GIT

CLASE 1

¿Qué es Git?
Git es un sistema de control de versiones distribuido que permite registrar cambios en un proyecto, trabajar en equipo y recuperar versiones anteriores.

¿Cómo nació Git?
Git fue creado en 2005 por Linus Torvalds, debido a que el proyecto Linux dejó de usar BitKeeper por problemas de licencia. Linus desarrolló Git en pocas semanas para gestionar el código de forma eficiente.

¿Cómo instalar Git?
Se descarga desde la página oficial: https://git-scm.com/downloads

En Linux:

Debian/Ubuntu: sudo apt-get install git
Fedora: sudo dnf install git
Arch: sudo pacman -S git

Verificación: git --version

Configuración inicial
Se debe configurar el usuario:

git config --global user.name "Nombre"
git config --global user.email "correo"

Archivos importantes en un repositorio

README.md: describe el proyecto
.gitignore: indica archivos que Git debe ignorar
LICENSE: define permisos de uso

CLASE 2

Estados de Git
Git maneja tres estados principales:

Directorio de trabajo (Working Directory):
Donde editas archivos.
Untracked: archivo nuevo sin seguimiento
Modified: archivo cambiado pero no preparado
Unmodified: sin cambios
Staging Area (Preparado):
Área donde eliges qué cambios irán al commit.
Repositorio local (Confirmado):
Donde se guardan los commits con historial.

Flujo de trabajo
Trabajas → agregas (add) → confirmas (commit)

Comandos básicos

git status → ver estado
git add <archivo> → enviar al stage
git add . → enviar todo
git restore <archivo> → deshacer cambios
git restore --staged <archivo> → quitar del stage
git commit -m "mensaje" → guardar cambios
git reset --soft HEAD~1 → deshacer último commit
git log --oneline → ver historial corto

.gitignore
Archivo que indica qué Git debe ignorar (ej: carpetas, temporales).

Buenas prácticas de commits

Hacer commits pequeños (atómicos)
Usar verbos imperativos: add, fix, change, remove
Máximo 50 caracteres
Sin punto final

Formato recomendado:

<tipo>: <descripción>

Prefijos:

feat: nueva funcionalidad
fix: corrección de errores
docs: documentación
style: formato
refactor: mejora de código
test: pruebas
build / ci / perf: técnicos

CLASE 3

¿Qué es GitHub?
GitHub es una plataforma en la nube basada en Git que permite almacenar repositorios, colaborar, compartir código y gestionar proyectos.

Git vs GitHub

Git: herramienta de control de versiones (local)
GitHub: plataforma donde se almacenan y comparten repositorios

SSH vs HTTPS

HTTPS: pide usuario y contraseña cada vez
SSH: usa una clave, no pide autenticación constante (más cómodo y seguro)

Configuración SSH

Generar clave:

ssh-keygen -t ed25519 -C "tu@email.com"

Ver clave:

cat ~/.ssh/id_ed25519.pub

Pasos:

Copiar clave
Ir a GitHub → Settings → SSH and GPG keys
New SSH key → pegar clave
Verificar:
ssh -T git@github.com

Crear repositorio en GitHub

Ir a Repositories → New
Poner nombre → crear

Conectar repositorio local a GitHub

git remote add origin git@github.com:usuario/repo.git
git branch -M main
git push -u origin main

Clonar repositorio

git clone git@github.com:usuario/repo.git

Con HTTPS:

git clone https://github.com/usuario/repo.git

Cambiar de HTTPS a SSH

git remote set-url origin git@github.com:usuario/repo.git

Ver repositorio remoto

git remote -v

Subir y bajar cambios

Subir:
git push origin main
Bajar:
git pull origin main

CLASE 4

git remote
Permite gestionar repositorios remotos (GitHub). Indica a Git dónde enviar y obtener cambios.

Comandos:

git remote -v → ver URLs remotas
git remote add origin "url" → vincular repo
git remote set-url origin "url" → cambiar URL

SSH múltiple
Permite usar varias cuentas de GitHub en una misma PC.

Pasos:

Crear nueva key:
ssh-keygen -t ed25519 -C "correo" -f ~/.ssh/otra_key
Configurar archivo ~/.ssh/config:
Host github-personal
 HostName github.com
 User git
 IdentityFile ~/.ssh/id_ed25519

Host github-trabajo
 HostName github.com
 User git
 IdentityFile ~/.ssh/otra_key
Verificar:
ssh -T git@github-trabajo
Clonar usando alias:
git clone git@github-trabajo:usuario/repo.git

Configuración local (por repositorio)
Permite usar distinto usuario en cada proyecto:

git config user.name "Nombre"
git config user.email "correo"

git checkout
Permite cambiar de rama o moverse entre commits.

Usos:

Cambiar rama:
git checkout rama
Crear y cambiar:
git checkout -b nueva_rama
Ir a un commit:
git checkout <hash>

Detached HEAD
Estado cuando te mueves a un commit y no estás en una rama:

No guardas cambios en una rama
Puedes perder cambios si no creas una rama

Para guardar:

git checkout -b nueva_rama

Buenas prácticas

No trabajar mucho en Detached HEAD
Hacer commit antes de cambiar de rama
Crear rama si vas a modificar
Mantener limpio el proyecto
