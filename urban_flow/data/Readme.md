
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

## Análisis de Multas y sus Evidencias (Imágenes)

El análisis del dataset de multas evidencia que, sobre un total de 1713 infracciones, 
solo 462 cuentan con evidencia visual asociada, lo que representa una cobertura visual limitada (cerca del 27%). 
Esto significa que la mayoría de las multas (en particular un volumen importante de las 1287 pendientes de pago, 
de las cuales solo 340 tienen imágenes relacionadas) no puede validarse de forma automática mediante análisis de 
imágenes, restringiendo el alcance del sistema de verificación automatizada.

En cuanto al desempeño técnico, la extracción de patentes con EasyOCR resulta aceptable sobre imágenes de buena 
calidad, pero pierde fiabilidad ante condiciones adversas como desenfoque, mala iluminación o ángulos pronunciados. 
En el presente trabajo se utilizaron como prueba imágenes suavizadas y en escala de grises después de que
las pruebas preliminares mostraron un mejor desempeño de detección para las mismas. La estrategia de comparar la patente
detectada contra la registrada mediante distancia de Levenshtein, junto con un umbral de coincidencia del 80%, aporta una 
tolerancia razonable a errores menores como la confusión entre caracteres similares (O/0, I/1). A esto se suman las 90 imágenes 
sin match, que reflejan los límites actuales del reconocimiento.

La separación entre tomas completas del vehículo y recortes de patente demostró ser acertada, ya que los recortes 
ofrecen mejores resultados al concentrar el texto en una mayor proporción de la imagen y requerir menos preprocesamiento.

En síntesis, el sistema constituye una base funcional a perfeccionar. Las mejoras más prometedoras pasan por incorporar 
un detector de regiones (contornos con más filtro geométrico) previo al OCR para elevar la precisión en imágenes completas, 
ampliar y diversificar el dataset visual para cubrir más variantes de iluminación y ángulos, restringir EasyOCR a caracteres 
alfanuméricos, y evaluar modelos de OCR especializados en patentes vehiculares. En conjunto, estas acciones permitirían aumentar
tanto la cobertura como la confiabilidad de la validación automática de infracciones.

## Análisis de la Última Etapa del Trabajo

El sistema de gestión de multas de tráfico ha sido exitosamente migrado a una base de datos relacional utilizando SQLAlchemy, lo que permite un manejo más estructurado y eficiente de la información. 

Se han identificado las patentes con mayor número de infracciones, destacando vehículos como 'WEFLYN' y 'HF3461' como reincidentes. Asimismo, los radares 'R01', 'R03' y 'R02' muestran ser los más activos en la detección de infracciones.

Un análisis del período 2020-2025 confirma la persistencia de ciertas patentes como reincidentes, como 'T0YDR' y 'XIIUME'. 

Finalmente, se ha determinado que aproximadamente el 26.97% de las multas cuentan con evidencia fotográfica, lo que resalta la importancia de la integración de datos visuales en el sistema aunque se podría mejorar la detección en imágenes en líneas futuras.
