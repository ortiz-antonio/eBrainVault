---
id: 202507222232
tags:
  - zk/fleeting
  - obsidian
  - ebrain
aliases: 
created: 2025-07-22T22:32:37-05:00
modified: 2025-07-23T15:11:41-05:00
---

---

## Sync obsidian with git on android and using a external keyboard

Estuve viendo métodos de sincronización entre obsidian de PC y Android, por que compre un teclado mecánico que adoro, y pensé que mi cel, puede ser un pequeño dispositivo ligero para tomar notas (Irónico que llame ligero por el peso de 1 kg de mi teclado) 
- El cel lo puedo poner fácilmente en cualquier lugar
- Esta nota, la estoy tomando a la vez que actualizo mi laptop, con debian 13 (Trixie)
- Con mis atajos de teclado, puedo mover fácilmente notas y usar mis templates de quick add.
- Me gusta el poder llevar mis notas conmigo, y poder estudiarlas, tal vez encontrar conexiones, para encontrar conexiones y mocs, ni siquiera ocupo el teclado fisico

## Bugs
- Actualmente tengo hotkeys directos para mi zk, de fleeting y permanent, usando la tecla win, sin embargo esta me abre la ventana de búsqueda de gémini, lo cierto es que puedo usar solo el hotkey de quick add y de ahí seleccionarlos.
	- Al tratar depiar una palabra entra en conflicto con ￼￼ctrl + shift ->￼￼, esto tambien me pasa en pc

## Solución
- Instale termux en android
- Instale el git con termux
- Cree una llave ssh con git
- Copie esa llave a mi mensajería que abrí en al PC, para darla de alta en mi cuenta de github
- Como la mayor parte del tiempo tengo acceso a mi teclado, o puedo esperar a llegar a casa para subir los cambios a git

## Problemas solucionados
### Problemas al hacer sync con git de modificaciones no relevantes en .obsidian
- Al abrir la app modifica workspace.json o workspace-mobile.json
- Lo mismo pasa cuando se abre los graph, modifica graph.json
## Solucion agregar a .gitignore

```
#Obsidian sync git

.obsidian/graph.json
.obsidian/workspace.json
.obsidian/workspace-mobile.json

```


### eliminar del repo

```
git rm .obsidian/workspace.json .obsidian/workspace-mobile.json .obsidian/graph.json -f

git add .

git commit -m "deleted workspace and graph json obsidian files from repo"

```

---
### Key Connections:
- [[Archives/Projects/obsidian-hotkeys/20250721155029_QuickAdd-Obsidian|20250721155029_QuickAdd-Obsidian]]