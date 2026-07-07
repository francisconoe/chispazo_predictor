# chispazo_predictor
Análisis predictivo para Chispazo usando co-ocurrencia avanzada (ventana 400, decaimiento 0.995), gaps, Monte Carlo y algoritmo genético. Genera 6 combinaciones, cubre 28 números, evita similitudes recientes y exporta a Excel con formato profesional. Basado en datos históricos reales.
Finalidad del Script
El script es una herramienta avanzada de análisis predictivo para el juego de lotería Chispazo (selección de 5 números del 1 al 28). Su objetivo principal es generar combinaciones de números con alta probabilidad estadística basándose en el historial de sorteos, empleando múltiples enfoques matemáticos y de inteligencia artificial.

Propósitos específicos:
Extraer patrones ocultos del historial de sorteos mediante análisis de co‑ocurrencia, gaps (atrasos), frecuencias y distribuciones reales.

Generar 6 combinaciones finales utilizando 6 métodos distintos para diversificar las estrategias y maximizar la cobertura de números (idealmente cubrir los 28 números posibles).

Evitar similitudes con sorteos recientes (últimos 333 sorteos) para no repetir combinaciones que ya aparecieron.

Ajustar automáticamente los filtros según el historial real (percentiles de sumas, distribuciones de tercios, cantidad de números primos) para que las combinaciones sean consistentes con el comportamiento histórico.

Entregar un reporte profesional en Excel con formato, colores, bordes y hojas adicionales (combinaciones repetidas) para facilitar la interpretación y toma de decisiones.

Metodología Utilizada
El script combina técnicas estadísticas, de optimización y aprendizaje computacional. Cada método genera una combinación candidata, y luego se aplica un proceso de optimización de cobertura para asegurar que entre todas se cubran la mayor cantidad de números posibles.

1. Análisis de Co‑ocurrencia Avanzada (Método principal)
Ventana temporal: últimos 400 sorteos con decaimiento exponencial (DECAIMIENTO = 0.995), dando más peso a sorteos recientes.

Matriz de co‑ocurrencia ponderada: calcula frecuencias de pares de números que aparecen juntos, normalizadas por el peso temporal.

Lift (medida de asociación): se exige un lift mínimo de 1.3 (30% más que el azar) para considerar un par como relevante.

Tres variantes de semilla:

Caliente: parte del número con mayor frecuencia ponderada.

Fría: parte del número con mayor gap (más sorteos sin aparecer).

Tripleta: parte de la tripleta de números con mayor frecuencia ponderada.

Construye la combinación agregando los compañeros con mayor lift a partir de la semilla.

2. Análisis de Gaps (Números atrasados)
Examina los últimos 500 sorteos para calcular el gap (número de sorteos transcurridos desde la última aparición) de cada número.

Genera combinaciones priorizando los números más atrasados y ajustando para que la suma se acerque al objetivo (percentil 75 de sumas históricas).

3. Simulación Monte Carlo
Con base en los últimos 800 sorteos, calcula las frecuencias individuales de cada número.

Realiza 3000 muestreos aleatorios ponderados por esas frecuencias, seleccionando la combinación que mejor se aproxime al objetivo de suma (percentil 90) y cumpla con los filtros de validación.

4. Algoritmo Genético
Utiliza los últimos 600 sorteos para definir el espacio de búsqueda.

Población inicial: generada aleatoriamente pero filtrada por las reglas de validación.

Función de fitness: premia combinaciones con suma cercana a la media histórica, distribución de tercios equilibrada (ej. 1‑2‑2), cantidad de primos entre 1 y 3, y que no hayan aparecido en el historial.

Operadores: selección de los mejores, cruce (mezcla de padres) y mutación (cambio de un número).

Ejecuta 40 generaciones y al final ajusta la combinación para acercarla al objetivo de suma (percentil 95).

5. Filtros de Validación Comunes
Distribución de tercios: se aceptan solo las distribuciones (1‑9, 10‑18, 19‑28) que hayan aparecido al menos en el 5% de los sorteos históricos.

Cantidad de primos: se permiten solo aquellas cantidades de números primos que aparecen en al menos el 5% de los sorteos.

Evitar similitudes: se descartan combinaciones que compartan 4 o más números con cualquiera de los últimos 333 sorteos.

6. Optimización de Cobertura Final
Una vez generadas las 6 combinaciones, se ejecuta un proceso iterativo (hasta 80 intentos) para reemplazar números repetidos por números que aún no han sido cubiertos, siempre que la nueva combinación siga pasando los filtros de validación.

El objetivo es lograr que entre las 6 combinaciones se cubran los 28 números posibles.

7. Generación del Reporte en Excel
Se escribe una hoja OUTPUT con las 6 combinaciones, indicando método, suma, diferencia con la media, estado (en rango/bajo/alto), cantidad de pares, primos y distribución por tercios.

Formato profesional: cabeceras con colores, bordes, alternancia de colores en filas y resaltado de celdas según el estado.

Se añade una hoja COMBINACIONES_REPETIDAS que detecta y lista aquellas combinaciones que han aparecido más de una vez en todo el historial, con sus fechas y concursos.
<img width="1153" height="671" alt="image" src="https://github.com/user-attachments/assets/354c289d-2cec-4f24-b495-51d03d110ae7" />
