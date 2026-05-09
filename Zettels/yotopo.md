---
id: 20260326151716
tags: 
---

---

# Yotopo
Generador minimalista basado en templates. Incluye design tokens en toml

[yotopo repo](https://github.com/ortiz-antonio/yopo)
[yoto dir](/home/ortiz/.utils/yopo)

Arquitectura framework agnostic, que maneje contenido, los design tokens y mis componentes de diseno.

De manera mas pragmatica pienso separar la generacion que descarga el template por default, a la generacion me crea la carpeta de proyecto con su .yotopo, tokens de ejemplo, contenido de ejemplo (Con su manera de consumir en ts en arquitectura hexagonal), donde puedo cambiar el template para usarlo de manera diferante.

Actualmente mi template en uso es:

[template uno astro](https://github.com/ortiz-antonio/template-tokens-uno-astro/)
Que esta en esta localmente en [folder template uno astro](/home/ortiz/Dev/template-tokens-uno-astro/)

## Refactor aplicado:
1.- Clono mi template tokens
2.- Hago un yopo init y me crea la carpeta yotopo con su arquitectura hexagonal dentro del framework

## Todo
-  Refactor taskfile por ejemplo el task donde se lee el project.toml, lo reuso en todas partes
- Refactor usar propiedad dir. de taskfile en lugar de estar haciendo prepent de {{.DIR}} en todos lados
- Al modificar un script de utopia, no me lanza el task de build-tokens, cuando deberia generar de nuevo el theme
#### Templates
- Tengo duplicado el uno.config
- El site.json no carga los datos, deja los del template
- Usar grids en lugar de media queries para el layout

### Comando sugerido: `yopo deploy`
Automatiza el despliegue local a una rama huérfana para mantener el repositorio limpio.
```bash
# Lógica interna de yopo deploy:
yopo build                     # Genera /dist en la raíz
git checkout --orphan dist     # Crea rama temporal sin historial
git add dist -f                # Fuerza la subida 1del dist (si está en .gitignore)
git commit -m "Deploy: $(date)"
git push origin dist --force   # Sube solo el build final
git checkout main              # Regresa al desarrollo
```

---

## Connections:
- [[]]

---

## Questions for Further Exploration:
- 