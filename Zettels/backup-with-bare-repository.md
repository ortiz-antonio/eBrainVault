---
id: 20250731183135
tags: 
---

---

# Backup my config files with bare repository
Para mejorar mi cambio de equipos, mas si me funciona el [[Zettels/proyecto-vender-laptop-dashboard|proyecto-vender-laptop-dashboard]] pense en respaldar mi configuracion, normalmente toco pequenas cosas, como el color del acento de gnome, acerlo en cada maquina, si me da flojera, ademas cada cambio, lo siento como una mejora en ergonomia.

## 1.- Crear un repositorio bare en  home
Un repositorio bare, permite solo crear la bd (.git) los archivos a rastrear se agregan manualmente a diferencia del repo standard
```
git init --bare $HOME/.dotfiles
```

## 2.- Agregar files
 Los archivos se agregan manualmente, usualmente median un alias al repo, por facilidad.
do
```
alias dotfiles='/usr/bin/git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'
```

En lugar del comando git, se usare el alias dotfiles, ejemplo `dotfiles status`

---


## 3.- Ocultar resto de archivos
Para enfocarnos solo en los archivos que agregamos a la bd: 
```
dotfiles config --local status.showUntrackedFiles no
```

## 4.- Agregar los primeros .dot
Agregar manualmente mediante el alias los .dot
```
dotfiles add .bashrc .zshrc .gitconfig .config/nvim/init.vim
```

## 5.- Usarlos en otra maquina
### Clonar
```
git clone --bare git@github.com:ortiz-antonio/.dotfiles.git $HOME/.dotfiles
```
###  Volver a crear el alias
[[#2.- Agregar files]]

### Resolver conflictos:
```
mkdir -p .dotfiles-backup
dotfiles checkout 2>&1 | grep -E "\s+\." | awk {'print $1'} | xargs -I{} mv {} .dotfiles-backup/
dotfiles checkout
```
## Connections:
- [Gestiona dotfiles](https://www.acuriousanimal.com/blog/2025-07-27-dotfiles-with-bare-repo/)

---

## Questions for Further Exploration:
- 