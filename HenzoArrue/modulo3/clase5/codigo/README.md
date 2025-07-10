# Optimización de Regresión Lineal con Métodos de Descenso de Gradiente

Este repositorio contiene un script de Python para demostrar y comparar diferentes algoritmos de optimización (Descenso de Gradiente, Descenso de Gradiente Estocástico y Adam) aplicados a un problema simple de regresión lineal. El objetivo es ajustar una línea a datos sintéticos y observar cómo cada algoritmo converge y se desempeña en términos de costo y trayectoria de parámetros.

## Contenido

  * `main.py`: El script principal que contiene la lógica para la generación de datos, los algoritmos de optimización, el cálculo del error y las funciones de visualización.

## Requisitos

- python 3.11.2
	- numpy
	- matplotlib

## Uso

El programa generará datos sintéticos, entrenará un modelo de regresión lineal utilizando Descenso de Gradiente (GD), Descenso de Gradiente Estocástico (SGD) y Adam, y luego mostrará tres gráficos:

1.  **Evolución del Costo:** Muestra cómo el Error Cuadrático Medio (MSE) disminuye a lo largo de las iteraciones para cada método.
2.  **Trayectoria de Parámetros:** Visualiza cómo los pesos ($w$) y sesgos ($b$) evolucionan durante el entrenamiento para cada método.
3.  **Líneas de Mejor Ajuste:** Muestra la línea de regresión final ajustada por cada método superpuesta sobre los datos generados.


## Funciones Clave

  * `generate_data(n=100, noise=1.0, seed=42)`: Genera $n$ puntos de datos sintéticos con una relación lineal y ruido gaussiano.
  * `mse(y, y_pred)`: Calcula el Error Cuadrático Medio entre los valores reales y predichos.
  * `gradients(x, y, y_pred)`: Calcula los gradientes de la función de costo (MSE) con respecto a los parámetros $w$ y $b$.
  * `train(x, y, method="gd", lr=0.01, iters=100, batch_size=1, beta1=0.9, beta2=0.999, eps=1e-8)`: Entrena el modelo de regresión lineal utilizando el método de optimización especificado. Soporta:
      * `"gd"`: Descenso de Gradiente (Batch Gradient Descent)
      * `"sgd"`: Descenso de Gradiente Estocástico
      * `"adam"`: Adam (Adaptive Moment Estimation)
  * `plot_cost(histories)`: Grafica la evolución del MSE para diferentes métodos.
  * `plot_params(w_hist, b_hist)`: Grafica la trayectoria de los parámetros $w$ y $b$ durante el entrenamiento.
  * `plot_fit(x, y, params)`: Grafica los datos generados y las líneas de mejor ajuste obtenidas por cada método.


## Metodología Empleada

Este proyecto implementa y compara tres algoritmos de optimización comúnmente utilizados en Machine Learning para entrenar un modelo de regresión lineal:

  * **Descenso de Gradiente (GD - Batch Gradient Descent):** Este método calcula el gradiente de la función de costo utilizando *todos* los puntos de datos en cada iteración. Esto garantiza una dirección de descenso precisa pero puede ser computacionalmente costoso para grandes conjuntos de datos.
  * **Descenso de Gradiente Estocástico (SGD):** A diferencia de GD, SGD calcula el gradiente y actualiza los parámetros utilizando *un solo punto de dato* (o un pequeño *mini-batch*) en cada iteración. Esto introduce más ruido en el proceso de optimización pero permite actualizaciones más frecuentes y rápidas, lo que puede ser beneficioso para conjuntos de datos muy grandes. La implementación en este código permite configurar el tamaño del *batch*.
  * **Adam (Adaptive Moment Estimation):** Adam es un algoritmo de optimización adaptativo que combina las ventajas de AdaGrad y RMSProp. Calcula medias móviles exponenciales de los gradientes (primer momento) y de los gradientes cuadrados (segundo momento). Estas estimaciones de momentos se utilizan para adaptar la tasa de aprendizaje para cada parámetro individualmente. Esto a menudo resulta en una convergencia más rápida y un mejor rendimiento en una amplia gama de problemas.

El proceso de entrenamiento para cada método implica:

1.  Inicializar los parámetros del modelo ($w$ y $b$).
2.  Iterar un número predefinido de veces:
      * Calcular las predicciones del modelo.
      * Calcular el error (MSE).
      * Calcular los gradientes del error con respecto a los parámetros.
      * Actualizar los parámetros utilizando la regla de actualización específica de cada algoritmo de optimización y una tasa de aprendizaje.
3.  Registrar el costo y la historia de los parámetros para su posterior análisis y visualización.
4.  Para cada modelo se utilizaron distintos argumentos, para poder comparar dos aspectos clave, la cantidad de **iteraciones** y el **learning rate**
  - GD
    - iters = 100
    - lr = 0.001

  - SGD
    - iters = 200
    - batch_size = 1
    - lr = 0.005

  - Adam
    - iters = 400
    - lr = 0.04

## Resultados Obtenidos y su Comparación

Al ejecutar el programa, se observarán resultados similares a los siguientes (los valores exactos pueden variar ligeramente debido a la aleatoriedad, aunque se usa una semilla para reproducibilidad):

**Salida de la Consola:**

```
GD:
w: 2.5693, b: 0.4401, MSE: 0.9775

SGD:
w: 2.5130, b: 1.2082, MSE: 0.9103

Adam:
w: 2.3860, b: 1.6389, MSE: 0.8583
```

**Análisis Visual de los Gráficos:**

  * **Evolución del Costo:**
      * **GD:** Muestra una curva de costo suave y consistentemente descendente. Esto se debe a que calcula el gradiente promedio sobre todos los datos, lo que lleva a un camino más estable hacia el mínimo.
      * **SGD:** La curva de costo de SGD suele ser más ruidosa y fluctuante. Esto se debe a que las actualizaciones de parámetros se basan en *batches* más pequeños o incluso en un solo punto, lo que introduce variabilidad. Sin embargo, a menudo puede escapar de mínimos locales más fácilmente y converger más rápido en las etapas iniciales, especialmente con grandes conjuntos de datos.
      * **Adam:** Generalmente, Adam muestra una convergencia rápida y eficiente. Su curva de costo suele ser suave como GD pero con una velocidad de descenso similar o superior a la de SGD en las primeras iteraciones, gracias a sus tasas de aprendizaje adaptativas.
  * **Trayectoria de Parámetros:**
      * **GD:** La trayectoria de $w$ y $b$ de GD es un camino directo y constante hacia los valores óptimos.
      * **SGD:** La trayectoria de SGD es más errática y "zigzagueante" debido a las actualizaciones basadas en *batches* pequeños y el ruido inherente.
      * **Adam:** La trayectoria de Adam es a menudo más directa y eficiente que SGD, moviéndose de manera más inteligente hacia la solución óptima gracias a sus tasas de aprendizaje adaptativas.
  * **Líneas de Mejor Ajuste:**
      * Los tres métodos convergen a líneas de mejor ajuste muy similares, lo que indica que son capaces de encontrar una buena solución para este problema de regresión lineal. Las diferencias en los valores finales de $w$ y $b$ son mínimas, lo que demuestra la robustez de estos algoritmos.
  * **Influencia de *iters* y *lr* :**
      * **Relación** : se concluye que cada algoritmo tiene su ámbito de aplicación, GD y SGD funcionan bien con una baja cantidad de datos, se aproximan bien al conjunto de puntos (datos), pero teniendo una tasa de aprendizaje (lr) más bien baja, es decir "aprenden lento", por otra parte Adam funciona muy bien con una mayor cantidad de datos teniendo una tasa de aprendizaje significativamente alta en comparación a los otros algoritmos.

## Reflexiones sobre la Importancia de la Tasa de Aprendizaje y la Elección del Método de Optimización en el Contexto de Machine Learning

### La Importancia de la Tasa de Aprendizaje (`lr`)

La **tasa de aprendizaje** (`lr`) es uno de los hiperparámetros más críticos en el entrenamiento de modelos de Machine Learning basados en optimización por gradiente. Determina el tamaño del paso que el algoritmo da en la dirección opuesta al gradiente de la función de costo.

  * **Tasa de aprendizaje demasiado alta:** Si la tasa de aprendizaje es muy alta, el algoritmo puede "saltar" sobre el mínimo, oscilando o incluso divergiendo y alejándose de la solución óptima. Esto se manifiesta en un costo que aumenta o es inestable.
  * **Tasa de aprendizaje demasiado baja:** Una tasa de aprendizaje muy baja hace que el algoritmo avance lentamente hacia el mínimo. Esto puede resultar en un entrenamiento excesivamente largo y computacionalmente costoso, e incluso puede llevar a que el algoritmo quede atrapado en un mínimo local o no converja en un tiempo razonable.
  * **Impacto en la convergencia:** Una tasa de aprendizaje bien ajustada permite que el algoritmo converja eficientemente al mínimo global (o a un mínimo local aceptable en problemas no convexos). En los métodos adaptativos como Adam, la tasa de aprendizaje global se ajusta internamente para cada parámetro, lo que reduce la necesidad de un ajuste manual tan fino.

### La Elección del Método de Optimización

La elección del método de optimización es fundamental y depende de varios factores:

  * **Tamaño del conjunto de datos:**
      * Para conjuntos de datos pequeños, **GD** puede ser una opción viable debido a su convergencia estable.
      * Para conjuntos de datos grandes, **SGD** o **Adam** son preferibles porque sus actualizaciones basadas en *batches* pequeños son mucho más eficientes computacionalmente.
  * **Complejidad del modelo y la función de costo:**
      * En problemas con funciones de costo no convexas (como en redes neuronales profundas), el ruido introducido por **SGD** a veces ayuda a escapar de mínimos locales y encontrar mejores soluciones globales.
      * **Adam** y otros optimizadores adaptativos suelen ser la elección por defecto en redes neuronales complejas debido a su capacidad para ajustar las tasas de aprendizaje por parámetro, lo que acelera y estabiliza el entrenamiento.
  * **Recursos computacionales:**
      * **GD** requiere almacenar todo el conjunto de datos en memoria para calcular el gradiente en cada iteración, lo que puede ser limitante.
      * **SGD** y **Adam** son más eficientes en el uso de memoria ya que procesan datos en *batches*.
  * **Velocidad de convergencia:**
      * **Adam** y sus variantes (como RMSProp, AdaGrad) suelen converger más rápido que GD o SGD puros, especialmente en problemas complejos, porque adaptan inteligentemente la tasa de aprendizaje.
      * **SGD** puede ser más rápido en las primeras etapas, pero su convergencia final puede ser más ruidosa.

En resumen, tanto la tasa de aprendizaje como la elección del optimizador son decisiones cruciales que impactan directamente en la eficiencia, estabilidad y rendimiento final de un modelo de Machine Learning. La experimentación y el ajuste fino de estos hiperparámetros son pasos esenciales en el ciclo de vida del desarrollo de modelos.

### Autor

Henzo Alejandro Arrué Muñoz

### Licencia

GPLv3