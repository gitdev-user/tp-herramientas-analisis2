
# Análisis del Dataset

## Análisis de Multas por Exceso de Velocidad

A partir del análisis del dataset de multas por exceso de velocidad, se identificaron diversos problemas de calidad de datos, tales como valores nulos, fechas y horas inválidas, y errores en el formato de algunas variables.

Estos inconvenientes fueron tratados mediante procesos de limpieza y normalización, permitiendo obtener un conjunto de datos consistente y apto para el análisis.

Se observó que una parte de los registros contiene valores imputados, como la fecha 1932-01-01 y la hora 00:00, los cuales representan datos inválidos en el origen. Este aspecto es importante, ya que impacta en la interpretación de los resultados.

En cuanto al comportamiento de las infracciones, se detectaron patrones relevantes:

- Existencia de patentes reincidentes.
- Concentración de multas en determinados horarios.
- Presencia de ubicaciones con alta frecuencia de infracciones.
- Niveles de exceso de velocidad que permiten dimensionar la gravedad de las multas.

Finalmente, se filtraron únicamente las infracciones reales, mejorando la calidad del análisis y asegurando resultados más confiables.
Este análisis aporta información valiosa para la toma de decisiones en materia de seguridad vial y control del tránsito.

