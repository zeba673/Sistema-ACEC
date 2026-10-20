# Sistema ACEC

> **Análisis de comportamiento en espacios cerrados**  
> Proyecto escolar para observar cómo se ocupa un espacio, con procesamiento completamente local.

ACEC busca estimar cuántas personas hay en un espacio, cuánto tiempo permanecen y qué puestos visitan. La persona que realiza la prueba podrá marcar y ajustar cada puesto sobre la imagen, en el SUM y en el momento.

## Cómo se espera que funcione

1. **Preparar el espacio:** abrir la vista de cámara y dibujar sobre la imagen las zonas correspondientes a los puestos expositores. Cada zona podrá nombrarse y ajustarse.
2. **Recolectar datos:** detectar y seguir personas de forma temporal para estimar la ocupación, las visitas y el tiempo de permanencia en cada puesto.
3. **Analizar los resultados:** después de un intervalo (por ejemplo, una hora) o al alcanzar cierta cantidad de personas detectadas, iniciar un análisis con IA ejecutada localmente.
4. **Mostrar estadísticas:** presentar en pantalla tanto las métricas calculadas como un resumen en lenguaje sencillo.

La recolección de datos es la tarea principal y debe tener prioridad. El análisis con IA es una etapa posterior, no necesaria para contar ni calcular las métricas básicas. Se buscará que no interrumpa la captura mientras trabaja.

## Puestos ajustables

Como la distribución real del SUM se definirá durante la prueba, los puestos no estarán preconfigurados. La interfaz debería permitir:

- Dibujar una zona encima de la imagen de la cámara.
- Asignarle un nombre, por ejemplo, “Puesto de ciencias”.
- Moverla, cambiar su tamaño o eliminarla durante la configuración.

## Estadísticas previstas

- Cantidad estimada de personas detectadas.
- Ocupación actual y visitas por puesto.
- Tiempo promedio de permanencia en cada puesto.
- Comparación de actividad entre puestos y a lo largo del tiempo.

Los resultados serán estimaciones. La cámara, la iluminación, las oclusiones y el movimiento de las personas pueden afectar el conteo y los tiempos.

## IA local y funcionamiento sin Internet

El objetivo es que el sistema funcione **sin conexión a Internet ni a otros equipos** durante la muestra. La cámara, la recolección de datos, el análisis y la visualización se ejecutarían localmente en la Raspberry Pi 5.

Como modelos candidatos para evaluar más adelante se mencionaron:

- Gemma 4 E2B
- Granite 4.2 2B
- Gemma 4 E4B

La elección queda pendiente de comprobar compatibilidad, memoria y velocidad en la Raspberry Pi 5. La IA recibiría las estadísticas recopiladas para ayudar a resumirlas; el diseño inicial no requiere que el modelo procese el video en vivo. Los nombres y requisitos de los modelos también se verificarán antes de implementarlos.

## Privacidad

La propuesta es procesar el video localmente y conservar estadísticas, sin guardar grabaciones ni identificar a las personas. Antes de una prueba real habrá que definir cómo informar a quienes estén en el SUM y qué datos conservar.

## Estado del proyecto

**Etapa:** definición de la idea y del alcance.

La Raspberry Pi 5 todavía necesita reinstalarse y la webcam aún no está disponible, así que el hardware y el rendimiento se probarán más adelante. Mientras tanto, se puede avanzar en el diseño de la interfaz, el formato de los datos y las métricas usando material de prueba.

## Objetivo

Crear una muestra escolar ajustable que ayude a entender cómo se distribuyen las visitas y la permanencia entre los puestos expositores del SUM, manteniendo todo el procesamiento en local.

---

*Documento vivo: el alcance y las decisiones técnicas se irán actualizando a medida que avance el proyecto.*
