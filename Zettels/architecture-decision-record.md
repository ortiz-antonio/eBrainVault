---
id: 20250821233811
tags: 
---
 
---

# Architecture Decision Record 
 Es un documento muy corto, generalmente un archivo Markdown, que captura una decisión
  arquitectónica importante. Sigue una plantilla simple:

   * Título: Un resumen de la decisión (ej. "Usar Nanostores para el manejo de estado").
   * Contexto: ¿Cuál era el problema o la situación que nos obligó a tomar una decisión? (ej.
     "Necesitábamos una forma de compartir el estado del temporizador entre componentes de UI
     sin acoplar la lógica de negocio a la UI").
   * Decisión: ¿Qué decidimos hacer? (ej. "Adoptaremos Nanostores como nuestra biblioteca de
     manejo de estado").
   * Consecuencias: ¿Cuáles son los resultados de esta decisión? (Positivas y negativas).
       * Positivas: "Es una biblioteca muy ligera. Se integra bien con nuestro enfoque de
         dominio desacoplado. Las pruebas son sencillas."
       * Negativas: "Añade una nueva dependencia al proyecto. El equipo necesita aprender su
         API."

  El Flujo de Trabajo del Arquitecto Práctico (C4 + ADRs)

  Este es el proceso que une todo lo que hemos hablado:

   1. Surge un Problema: El equipo necesita decidir cómo manejar el estado en la aplicación
      Pomodoro.
   2. Pensamiento Visual (Usando C4): Como arquitecto, abres tu diagrama de Componentes (Nivel
      3). Dibujas diferentes opciones.
       * Opción A: La UI habla directamente con el Dominio y este le devuelve el estado. (Ves
	         que esto crea un acoplamiento fuerte).
       * Opción B: Introduces un nuevo componente, el "Gestor de Estado". La UI se suscribe a
         él, y el Dominio lo actualiza. (Ves que esto respeta la Regla de la Dependencia de la
         Arquitectura Limpia).
       * El diagrama te ayuda a ver las consecuencias estructurales de cada opción.

   3. Toma de Decisión: El equipo elige la Opción B.
   4. Registro de la Decisión (Crear el ADR): Creas un nuevo archivo,
      001-use-nanostores-for-state-management.md. Llenas la plantilla explicando el contexto, la
      decisión y las consecuencias. Puedes incluso enlazar o incrustar el mini-diagrama que
      usaste para decidir.
   5. Actualización del Mapa (Actualizar C4): Actualizas tu diagrama de Componentes C4 "oficial"
      para que refleje la nueva realidad: ahora incluye el componente "Gestor de Estado".

  ¿Por Qué Esto Encaja Contigo?

   * Un ADR es un Zettel: Es una nota atómica, enfocada en una sola decisión, que captura el
     "porqué". Tu eBrainVault podría tener una carpeta /ADRs para tu proyecto Pomodoro.
   * Refuerza la "Claridad Estructural": No solo tienes el mapa (C4), sino también la historia y
     la justificación de por qué el mapa es como es (ADRs).
   * Es la Práctica del "Arquitecto Constructor": Este flujo de trabajo es la evidencia tangible
     del rol que describimos. Es la prueba de que no solo codificas, sino que diseñas, justificas
      y documentas las decisiones que guían el desarrollo.

  Este ciclo de Visualizar (C4) -> Decidir -> Registrar (ADR) es el corazón del diseño de
  software ágil y evolutivo.

---

## Connections:
- [[Zettels/software-arquitecture|software-arquitecture]]

---

## Questions for Further Exploration:
- 