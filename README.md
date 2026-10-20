# Sistema ACEC

> **Análisis de comportamiento en espacios cerrados**  
> Proyecto escolar para observar, de forma anónima, cómo se ocupa un espacio.

ACEC busca usar una cámara web conectada a una **Raspberry Pi 5** para estimar cuántas personas hay en un espacio, cuánto tiempo permanecen y qué zonas visitan. La persona que realiza la prueba podrá marcar y ajustar esas zonas en el momento, directamente sobre la imagen de la cámara.

Este README es el punto de partida del proyecto. La idea, el alcance y las decisiones técnicas se irán completando a medida que avance el trabajo.

---

## ¿Qué se quiere observar?

- **Ocupación:** cantidad estimada de personas en el espacio y en cada zona.
- **Permanencia:** tiempo aproximado que cada persona detectada pasa en una zona.
- **Recorrido por zonas:** qué puestos o áreas se visitan y durante cuánto tiempo.

El sistema se plantea como una herramienta de observación del espacio, no de identificación de personas.

## Zonas ajustables

Como el lugar de prueba no está definido de antemano, las zonas no deberían quedar fijas en el programa. La idea es poder:

1. Ver la imagen en vivo.
2. Marcar una zona sobre la imagen.
3. Ponerle un nombre, por ejemplo, “Puesto 1” o “Entrada”.
4. Moverla, cambiar su tamaño o eliminarla durante la configuración.

Así se podrán definir los puestos en el momento, según el espacio real.

## Primera versión imaginada

Una primera muestra podría incluir:

- Vista en vivo de la webcam.
- Herramienta sencilla para dibujar y editar zonas.
- Detección y seguimiento temporal de personas para evitar contarlas de nuevo en cada imagen.
- Conteo actual por zona y medición aproximada de permanencia.
- Resumen visible de los resultados.

La cámara considerada inicialmente es una webcam USB Raptor Vision 4K. Su compatibilidad con Raspberry Pi OS todavía debe comprobarse en el equipo. Para este proyecto, que la cámara funcione de forma estable importa más que aprovechar la resolución 4K.

## Privacidad y límites

La propuesta inicial es procesar la imagen localmente en la Raspberry Pi y guardar estadísticas, no grabaciones de video ni identidades. El conteo y la permanencia serán estimaciones: la posición de la cámara, la iluminación, las oclusiones y la distancia entre personas pueden afectar los resultados.

Antes de una prueba real, habrá que acordar cómo informar a las personas presentes y qué datos conservar.

## Estado

**Etapa:** definición de la idea y del alcance.

Todavía faltan decisiones como la interfaz que se usará para configurar las zonas, el formato de los resultados, las condiciones de prueba y el método de detección. Se irán incorporando a este documento cuando queden definidas.

## Objetivo del proyecto

Construir una muestra escolar clara y ajustable que ayude a entender cómo se distribuyen y se mueven las personas dentro de un espacio cerrado.

---

*Documento vivo: esta descripción irá cambiando junto con el proyecto.*
