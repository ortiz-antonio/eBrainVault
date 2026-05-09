---
id: 20250820193119
tags: 
---

---

# Software Arquitecture

Trataba de hacer la arquitectura mientras escriba el codigo, esto es altamente infeciente, al adaptar mi mente a usar zettelkasten ahora lo veo en terminos de conocimiento vivo: Un fleeting es un componente, al estar dentro del diagrama de software pasa a ser un zettel, el diagrama viene siendo el equivalente a un moc.

## Agile
No ocupo procesar todos los requerimientos a la vez, necesito identificar los impulsores. Son los que definen la arquitectura y un cambio en estos puede romper la arquitectura, en cambio los componentes son los que viven dentro de la arquitectura.
### Plan de liberacion
Aqui creo el plan con tiempos y lo que contiene cada version.

## Prototipado de arquitectura
El prototipado de arquitectura lo hago con stubs and fakes, pienso en terminos de relaciones entre componentes, no en implementacion.

### Cli first
Me permite probar el software sin la complejidad de hacer una ui completa, ademas da al software la capacidad de correr de manera eficiente desde la terminal, de esta manera puedo probar la integracion completa de la [[#Plan de liberacion]]

## VSD
Siguiendo el [[#Plan de liberacion]] desarrollo de manera concurrente logica + ui, para entregar valor visible diariamente,  siguiendo un [[Zettels/daily-delivery|daily-delivery]]

## Documentar desiciones
Documentar desiciones mediante [[Zettels/architecture-decision-record|architecture-decision-record]]

---

## Connections:
- [[Zettels/c4|c4]]
- [[Zettels/architecture-decision-record|architecture-decision-record]]

---

## Questions for Further Exploration:
- 