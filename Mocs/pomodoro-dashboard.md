---
id: 20250818160000
tags:
- project
- pomodoro
- dev
- astro
- hexagonal-architecture
---

# Dashboard del Proyecto: Pomodoro Right

Este es el centro de mando para el proyecto del temporizador Pomodoro.

## Arquitectura
[[Mocs/pomodoro-arquitectura-moc|pomodoro-arquitectura-moc]]
## Contexto y Principios

Este proyecto es un campo de práctica para aplicar y refinar mi [[Zettels/modelo-relaciones-profesionales|modelo de relaciones profesionales]], enfocándome en construir un portafolio de alta calidad.
Asi como tambien evaluar si es viable un uSass [[Mocs/pomodoro-uSass-moc|pomodoro-uSass-moc]] con [[Zettels/pomodoro-market-fit-obsidian-zk-pomodoro-current-title|pomodoro-market-fit-obsidian-zk-pomodoro-current-title]]

## Inventario del Proyecto

- **Ubicación:** `/home/ortiz/Dev/pomodoro-right`
- **Propósito:** Un temporizador Pomodoro simple, enfocado y con modo oscuro.
- **Estado:** Repositorio Git limpio, en la rama `main`.

### Arquitectura y Tecnología

El proyecto está construido siguiendo prácticas modernas de desarrollo de software para asegurar calidad y mantenibilidad.

- **Arquitectura Principal:** **Arquitectura Hexagonal**. La lógica de negocio (`src/domain`) está completamente desacoplada de la interfaz y los servicios externos.
- **Metodología de Desarrollo:** **TDD (Test-Driven Development)**. Toda la lógica es validada con pruebas antes de ser implementada.
- **Frontend:** **Astro**. Un framework moderno y rápido para construir sitios web.
- **Manejo de Estado:** **Nanostores**. Una biblioteca pequeña y eficiente para el estado global.
- **Testing:** **Vitest**. Un framework de pruebas unitarias rápido y moderno.

### Estructura de Carpetas Clave

- `src/domain`: Contiene la lógica pura del pomodoro (entidades, servicios). Es el corazón de la aplicación.
- `src/adapters/astro`: Contiene la interfaz de usuario (UI) y la capa de presentación.
- `src/tests`: Contiene todas las pruebas unitarias que garantizan el correcto funcionamiento del dominio.

## Ideas
[[Zettels/pomodoro-keyboardfirst|pomodoro-keyboardfirst]]