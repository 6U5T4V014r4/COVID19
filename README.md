# Desarrollo de diferentes modelos y métodos matématicos para discribir la presente pandemia de Coronavirus COVID19 y SARS-CoV-2

El presente trabajo se base en dos modelos anteriores: 

- https://github.com/Rank23/COVID19
- https://github.com/JeroenKools/covid19

Los resultados se pueden observar en el siguiente python notebook: 

- https://github.com/ypriverol/COVID19/blob/master/Cuba/Cuba%20Ciencia%20-%20COVID%20Forcast..ipynb

Los resultados se corren diariamente por @ypriverol. 

### Primera parte: Estudio Descriptivo

En la primera parte del estudio se ven gráficos que describen el el progreso de la epidemia en diferentes partes del mundo. 

- Crecimiento logarítmico en los 10 países más afectados
- Crecimiento logarítmico en los los países de Centro América y el Caribe 
- Velcocidad de Crecimiento de la pandemia: Cantidad de casos cada 3 días. 

### Segunda parte: Predicción empleando Kalman Filter 

El filtro de Kalman es un algoritmo desarrollado por Rudolf E. Kalman en 1960 que sirve para poder identificar el estado oculto (no medible) de un sistema dinámico lineal, sirve además cuando el sistema está sometido a ruido blanco aditivo.

El presente modelo permite entender los datos en un evento dinámico (que cambia constantemente) y predecir cual es el valor que sigue (en este caso los posibles nuevos casos) a corto plazo. En el caso de un evento epidemiológico donde existen tantas variables como: nivel de contacto de la población, medidas de distanciamiento y mitigación tomados por el estado, el número básico de reproducción del virus SARS-CoV-2.

Este modelo ha sido propuesto inicialmente por: https://github.com/Rank23/COVID19

### Tercera parte: Predicción empleando R0, medidas de mitigación

Los siguientes modelos presentan 3 simulaciones siendo la única diferencia la efectividad de las medidas de distanciamiento, y el confinamiento absoluto.

Confinamiento efectivo: Asume condiciones normales al comienzo, seguido de un bloqueo rápido y muy estricto durante el tiempo que sea necesario. Este es el mejor caso, pero poco probable.

Confinamiento ineficaz: Se realiza un intento tardío y poco entusiasta de confinamiento, pero el virus sigue propagándose a media velocidad. Esto sería bastante malo; la mayoría de la población se infectaría antes de que una vacuna esté disponible.

Medidas y batalla prolongada: los períodos alternos de bloqueos estrictos con períodos más relajados suavizan el golpe a la economía y detienen la cantidad de infecciones hasta que se pueda desarrollar una vacuna, o hasta que finalmente se active la inmunidad colectiva.

Tenga en cuenta que esto es muy especulativo y altamente dependiente de:

El valor elegido para el factor de mitigación. Junto con R0, esto representa los efectos de cuarentenas, confinamiento y otras contramedidas, y determina la tasa reproductiva efectiva.
Si R0 es 2, el factor de mitigación es 0.8, y el 98% de la población aún no ha sido infectado, Reff = 2 0.8 0.98 = 1.568, lo que significa que efectivamente, cada 1000 personas infectadas propagarán la enfermedad a un promedio de 1568 personas no infectadas.
La entrada para el factor de mitigación es una lista que se interpola a la misma longitud que la cantidad de días para simular. Por ejemplo, simulando 5 días con una tendencia de mitigación de [1.0, 0.8] utilizará tasas de crecimiento de [1.0, 0.95, 0.90, 0.85, 0.80]. El valor elegido para la tasa de letalidad (cfr); la evidencia hasta ahora sugiere un rango de 0.01 a 0.06

Otras limitaciones de la simulación:

No considera el tiempo de incubación
No tiene en cuenta los viajes internacionales y la posible recontaminación / resiembra para las segundas y posteriores olas.
No considera el efecto sobre la tasa de mortalidad cuando el número de casos activos supera la capacidad.



