---
id: 20260402164500
tags:
  - superadobe
  - hardware-libre
  - ingenieria
  - comunidad
---

# Superadobe Vertical Ram Extruder (VRE) - Diseño v1.0

Este diseño representa el salto de "herramienta de taller" a "maquinaria de producción comunitaria". Utiliza un ciclo de **extrusión por ariete (Ram Extrusion)** para compactar mezclas de tierra directamente en costales de gran formato (50kg).

## 1. Concepto Operativo: El Ciclo de Ariete
A diferencia de un tornillo sin fin, el ariete (pistón) permite una fuerza de compactación masiva y es inmune a la abrasión de la arena.

1. **Fase de Carga (Retracción):** El pistón sube por encima de la apertura de la tolva. La tierra cae por gravedad al cilindro de compresión.
2. **Fase de Compresión (Empuje):** El pistón baja, sella la tolva y empuja la dosis de tierra hacia la boquilla (die).
3. **Salida:** La tierra sale pre-compactada en forma de "chorizo" continuo, llenando el costal que "viste" la boquilla.

---

## 2. Componentes Críticos (Arquitectura Técnica)

### A. El Motor de Fuerza: Gato Mixto (Hidro-Pneumático)
* **Tipo:** Gato de botella para grúa (long ram jack) de 8-12 toneladas.
* **Ventaja:** Conexión a compresor de aire para velocidad (ciclos rápidos) y palanca manual para precisión o máxima fuerza en mezclas secas.

### B. El Cuerpo de Compresión (Cilindro y Tolva)
* **Cilindro:** Tubo de acero de pared gruesa (Cédula 40 o 80) de 6" a 10" de diámetro.
* **Tolva Lateral:** Diseño de "pared caída" (una cara vertical, otra inclinada a 60°) para evitar el puenteo de la tierra.
* **Plato del Ariete:** Disco de acero reforzado con un "sello de sacrificio" de polietileno (HDPE) o madera dura para proteger las paredes del cilindro de la arena.

### C. La Boquilla de Salida (Die)
* **Intercambiable:** Permite cambiar entre "chorizos" anchos para casas y delgados para detalles o maquetas.
* **Conicidad:** Ligero ensanchamiento al final (1-2 grados) para reducir la fricción de salida.

---

## 3. Lista de Materiales (Recuperables/Soberanía)
* [ ] **Gato Hidráulico:** Gato de aire/hidráulico de 12 ton (común en prensas de taller).
* [ ] **Estructura:** Perfiles en "H" o "U" de acero (Vigas de recuperación).
* [ ] **Cilindro:** Tramo de tubería industrial de 8" (sobrantes de construcción civil).
* [ ] **Resortes de Retorno:** Para ayudar al gato a subir rápido en la fase de carga.
* [ ] **Vibrador de Tolva:** Motor de 12V con masa descentrada (opcional, para flujo continuo).

---

## 4. Ventajas para la Comunidad eBrain
* **Costo de Entrada:** Construible con materiales de chatarra y un gato comercial.
* **Mantenimiento:** Bajo. Las piezas de desgaste (HDPE del pistón) son fáciles de reemplazar.
* **Ergonomía:** Permite construir un horno o casita de perro en una fracción del tiempo manual, sin el agotamiento físico del pisón tradicional.

---

## Connections:
- [[Mocs/superadobe-moc]]
- [[Zettels/superadobe-prototipo-maquina]]
- [[Zettels/entornos-de-valor]] (Colaboración con papá)

## Questions for Further Exploration:
- ¿Cuál es la presión PSI ideal del compresor para mantener un ritmo de 5 ciclos por minuto?
- ¿Podemos diseñar un soporte de costal que se ajuste automáticamente según el peso?
