<a href="https://www.eii.ulpgc.es" target="_blank"><img src="https://www.eii.ulpgc.es/sites/default/files/eii-acron-mod.png" alt="EII-ULPGC" align="right" width="516" height="150" /></a>
# PRÁCTICA FINAL DE SRA: COMPETICIÓN
> - Desarrollo de un robot con capacidad de detectar, seguir y evitar obstáculos en un entorno determinado
> - Proyecto desarrollado por Miguel Escobedo Santana, Eduardo Ortega Zerpa, Micael Guerra Rodríguez, Miguel Ángel Peñate Alemán e Imanol Benito Quintero Bermúdez

## Descripción general

Este proyecto, realizado para la asignatura **Sistemas Robóticos Autónomos**, del último curso del Grado en Ingeniería Informática de la Universidad de Las Palmas de Gran Canaria, tiene como objetivo desarrollar un robot autónomo utilizando las herramientas *LEGO Mindstorms EV3*. El robot, bautizado como *KITT, el coche fantástico*, en referencia a la famosa serie de televisión, pretende competir en un escenario diseñado para evaluar su capacidad de detección, navegación y estacionamiento en paralelo. La competición incluye dos obstáculos cilíndricos separados 40 centímetros entre sí, y una línea en el suelo que conecta ambos. Según el planteamiento del grupo, el robot debe:

- Detectar el primer obstáculo.
- Evitarlo de manera segura.
- Encontrar el segundo obstáculo.
- Posicionarse entre ambos con cada rueda a un lado de la línea.

Mediante el uso de la librería *ev3dev2*, el sistema permite emplear un enfoque modular que integra sensores ultrasónicos, sensores de color y motores, controlados a través de scripts en *Python*.

## Pasos realizados

1. Detección de obstáculos: el robot realiza un barrido angular utilizando el sensor ultrasónico para identificar el obstáculo más cercano.

2. Seguimiento de obstáculos: el robot se aproxima a los obstáculos calculando dinámicamente la distancia segura. En caso de perder el objetivo, se trata de reorientar hacia el obstáculo detectado inicialmente.

3. Evitación de obstáculos: el robot utiliza un algoritmo heurístico para esquivar los obstáculos girando hacia un lado y avanzando una distancia predefinida antes de retomar la búsqueda del siguiente objetivo.

4. Detección de la línea: el sensor de color opera para identificar la línea en el suelo.

5. Estacionamiento final: tras identificar la línea, el robot se posiciona entre los obstáculos y ajusta su orientación mediante giros para completar el estacionamiento en paralelo, y que ambas ruedas se posicionen a los lados de la línea.

## Características técnicas

### Sensores empleados

- Ultrasónico: detecta obstáculos mediante ondas sonoras.

### Color

Identifica la línea en el suelo y mide la intensidad de luz reflejada.

### Control de motores

Implementado en la clase *RobotMovement*, que abstrae la lógica de giros, movimientos lineales y paradas abruptas.

### Robustez

Mecanismos de recuperación de errores para superar problemas comunes, como lecturas inexactas del sensor ultrasónico y cambios en las condiciones de iluminación.

### Código principal

El archivo principal, *parallel_parking.py*, coordina las funciones críticas del robot:

- *find_obstacle*: realiza un barrido angular para localizar obstáculos.
- *follow_obstacle*: mantiene una distancia constante respecto al obstáculo detectado.
- *avoid_obstacle*: esquiva el obstáculo girando y avanzando estratégicamente.
- *find_line*: localiza la línea final y ajusta la posición del robot.

### Ejecución del programa

```sh
python3 parallel_parking.py
```

El robot emite una señal sonora al inicio y al final de la ejecución, indicando el tiempo total empleado para completar la tarea.

## Resultados obtenidos

El robot cumplió con los objetivos establecidos, y completó la tarea de forma exitosa en las pruebas. Las principales dificultades encontradas fueron:

- Detección irregular de obstáculos con superficies curvas.
- Sensibilidad del sensor de color.
- Ajustes en las velocidades de los motores para reducir errores.
