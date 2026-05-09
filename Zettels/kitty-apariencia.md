---
id: 202507200006070500
tags: kitty
---

# Configuración de Kitty

Este Zettel documenta la configuración personalizada del emulador de terminal [Kitty](https://sw.kovidgoyal.net/kitty/). La idea es tener una terminal limpia, rápida y que se sienta cómoda para programar.

Empece a usar kitty para tener una mejor navegacion la usar gemini-cli, por que no podia usar linea por linea, por que en el prompt, regresaba a respuestas anteriores, aunque eso lo solucione ya, con los atajos mapeados de [[Zettels/via-custom-maps#Navegación y Sistema]] para usarlo en gnome-shell, browser y apps, me quedo con kitty por la facilidad que tiene de trabajar con el teclado y la personalizacion.

## Mi Configuración (`kitty.conf`)

```
# BEGIN_KITTY_FONTS
font_family      family="Noto Mono"
bold_font        auto
italic_font      auto
bold_italic_font auto
# END_KITTY_FONTS
font_size 14.0
```

## Reflexiones

Me encanta como se ve `Noto Mono` en la terminal. Es limpia, clara y perfecta para el código. Lo curioso es que esta misma fuente que se siente tan bien aquí, en Kitty, para programar, se sentía rarísima en Obsidian para leer. Es un buen recordatorio de que cada herramienta tiene su contexto y su configuración ideal. Lo que funciona para código no necesariamente funciona para la lectura de párrafos largos.

## Relacionados
- [[Zettels/kitty-hotkeys|kitty-hotkeys]] 
- [[Zettels/tema-apps|tema-apps]]