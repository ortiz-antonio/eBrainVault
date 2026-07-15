---
id: 20260715103041
tags: 
---

---

# Nube Local
Analizare el tener una nube local para respaldar mis recuerdos y fotos, sin que esten disponibles en internet.
Para las fotos que quiero conservar lo primero es la seguridad


---

## Hardware
Me suena mejor una mini pc que convine nas "Mini PC NAS" o "AIO NAS"

---

## Software
- TrueNas
- OpenMediaVault

---

## Fricciones
- Un dispositivo que ocupa mantenimiento y actualizaciones, rompe el [[Zettels/minimalismo|minimalismo]] 
- Sin embargo, no veo otra manera de mantener fotos privadas,


---

## Alternativas
- Respaldo fisico: Pero no se integra con el celular para respaldo, anade pasos extras para la transferencia

---

## Opción C (IA): "El Protocolo Manual Optimizado"

  Si decides que no quieres ningún software corriendo en segundo plano:

  • Un SSD externo robusto (tipo SanDisk Extreme) + cable directo al celular.
      • Una vez a la semana/mes, conectas el SSD directamente al puerto USB-C de tu celular y copias la carpeta de
      fotos.
      • Fricción: Es manual (rompe la automatización), pero es el estado máximo de minimalismo: no hay sistema
      operativo, no hay red, no hay actualizaciones, no hay consumo eléctrico.

---

## Opción 3: Un Hub/Gabinete Con RAID Por Hardware Integrado (Cero cOnfiguración dE rEd)

  Si no quieres configurar nada a nivel de comandos de Linux en el router, puedes delegar la duplicación al propio
  chasis de los discos:

  1. El Hardware: Compras un Gabinete Dual USB tipo RAID de bolsillo (marcas como Terramaster, Yottamaster o Sabrent
  venden gabinetes muy pequeños para 2 unidades SSD SATA de 2.5" o M.2).
  2. Cómo funciona: Estos gabinetes tienen un interruptor físico (switch) detrás. Lo colocas en modo RAID 1.
  3. La Conexión: Colocas los dos SSDs dentro del gabinete y conectas el cable USB del gabinete directamente al
  router.
  4. Resultado: Para el router de viaje, ese gabinete se comporta exactamente como si fuera un solo SSD externo común
  y corriente. La duplicación la hace el chip interno del gabinete. Cero mantenimiento para ti.
---

## Opcion 4
dual M.2 NVMe SSD enclosure hardware RAID 

---

## Hasta Ahora
SI bien, es una necesidad, mantener un servidor privado me anade complejidad que no quiero, sin embargo si no lo resuelvo mantendre el problema de la privacidad.

Lo mas minimalista es un enclosure con raid para 2 ssds, sin embargo tengo una resistencia interna, aunque es mas privado  y seguro, siento la friccion de no usar las herramientas integradas de los dispositivos para sincronizacion

---

## Connections:
- [[]]

---

## Questions For Further Exploration:
- 