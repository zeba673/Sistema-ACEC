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

### Candidato inicial: Granite 4.2 3B

Como primer modelo para probar se propone **`granite4.2:3b` en una cuantización liviana, ejecutado con Ollama**.

Se elige como candidato inicial porque:

- Su variante 3B publicada en la biblioteca de Ollama ocupa aproximadamente **2,2 GB en disco**. Esto describe el archivo del modelo; no es una medida de la RAM total que usará al ejecutarse.
- Granite 4.2 declara soporte para español y salida estructurada en JSON, útil para convertir métricas numéricas en resúmenes consistentes.
- Solo se le pasarían estadísticas agregadas (por ejemplo, visitas y permanencia por puesto), no el video en vivo. No necesitamos sus capacidades de imagen para esta tarea.
- Su archivo cabe holgadamente en el SSD SATA de 480 GB, que también permite conservar el sistema y los datos locales de la muestra.

La Raspberry Pi 5 tiene **16 GB de RAM**, pero esa memoria también la necesitan el sistema, la interfaz y el proceso de visión. El tamaño del archivo no garantiza que el modelo vaya a responder rápido: la velocidad real de inferencia en la Pi todavía debe medirse. Por eso, la IA se ejecutaría por lotes tras un intervalo o un umbral de datos, y la captura deberá conservar prioridad.

**Alternativas para comparar:** Gemma 4 E2B y Gemma 4 E4B. Gemma 4 ofrece modelos pequeños orientados a dispositivos de borde, pero E2B/E4B tienen variantes de Ollama más pesadas en disco que Granite 4.2 3B. Se probarán solo si Granite no produce resúmenes suficientemente útiles en español.

> La elección es provisional. Antes de la muestra se comprobarán instalación sin Internet, consumo de memoria, tiempo de respuesta y efecto sobre la captura en la propia Pi 5. El modelo y sus dependencias se descargarán previamente; el día de la prueba no se dependerá de Ollama Cloud ni de ningún servicio externo.

## Privacidad

La propuesta es procesar el video localmente y conservar estadísticas, sin guardar grabaciones ni identificar a las personas. Antes de una prueba real habrá que definir cómo informar a quienes estén en el SUM y qué datos conservar.

## Estado del proyecto

**Etapa:** definición de la idea y del alcance.

La Raspberry Pi 5 todavía necesita reinstalarse y la webcam aún no está disponible, así que el hardware y el rendimiento se probarán más adelante. Mientras tanto, se puede avanzar en el diseño de la interfaz, el formato de los datos y las métricas usando material de prueba.

## Objetivo

Crear una muestra escolar ajustable que ayude a entender cómo se distribuyen las visitas y la permanencia entre los puestos expositores del SUM, manteniendo todo el procesamiento en local.

---

*Documento vivo: el alcance y las decisiones técnicas se irán actualizando a medida que avance el proyecto.*
