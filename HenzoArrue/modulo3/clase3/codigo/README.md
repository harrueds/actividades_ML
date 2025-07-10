# Derivación, Visualización y Optimización de Funciones en Python

## Resumen del Proyecto

Este proyecto tiene como objetivo aplicar los conceptos fundamentales del cálculo diferencial en una variable para la derivación simbólica, la identificación de puntos críticos y la optimización de funciones utilizando las librerías de Python: SymPy, NumPy, Matplotlib y SciPy. El problema central es analizar la función $f(x) = (x-3)^2$, encontrar su punto de minimización y visualizar este proceso.

## Estructura del Proyecto

El código está organizado en funciones modulares, cada una con un propósito específico:

1.  **`derivacion_simbolica_y_puntos_criticos()`**: Encargada de la definición simbólica de la función y su derivada, así como de la resolución de la ecuación $f'(x) = 0$ para encontrar el punto crítico.
2.  **`visualizar_funcion_y_derivada()`**: Se encarga de generar los gráficos de la función original $f(x)$ y su derivada $f'(x)$, marcando visualmente el punto crítico donde se alcanza el mínimo.
3.  **`optimizacion_numerica()`**: Utiliza la función `minimize` de SciPy para encontrar numéricamente el mínimo de la función y compara este resultado con el obtenido simbólicamente.

## Decisiones de Diseño y Relevancia en Machine Learning

### 1. Definición y Derivación Simbólica (SymPy)

* **Decisión de Diseño**: Se eligió `SymPy` para la manipulación simbólica de la función. Esto permite definir `x` como un símbolo y aplicar operaciones de cálculo como la derivación de manera precisa, sin preocuparse por la discretización o errores numéricos. La `regla de la cadena` se aplica automáticamente por `SymPy` durante la derivación. La resolución de `f'(x) = 0` también se realiza simbólicamente para encontrar el punto crítico exacto.
* **Relevancia en ML**: En Machine Learning, muchos algoritmos de optimización (como el Descenso de Gradiente) se basan en el cálculo de derivadas. La capacidad de obtener derivadas exactas es fundamental para entender cómo los cambios en los parámetros afectan la función de costo y para depurar algoritmos de optimización.

### 2. Visualización de la Función y su Derivada (Matplotlib)

* **Decisión de Diseño**: `matplotlib` se utilizó para graficar tanto la función $f(x)$ como su derivada $f'(x)$ en el rango `[-5, 10]`. Se marcó el punto crítico (`x=3`) en el gráfico de $f(x)$ para resaltar visualmente dónde la función alcanza su mínimo y dónde la derivada cruza el eje x (indicando una pendiente cero).
* **Relevancia en ML**: La visualización es crucial para entender el comportamiento de las funciones de costo y el impacto de los gradientes. Permite a los desarrolladores y científicos de datos observar si los algoritmos de optimización se están moviendo en la dirección correcta y si están convergiendo a un mínimo. Graficar la derivada ayuda a comprender cómo la "pendiente" de la función guía el proceso de optimización.

### 3. Optimización Numérica (SciPy)

* **Decisión de Diseño**: La función `scipy.optimize.minimize` fue empleada para encontrar numéricamente el valor de `x` que minimiza $f(x)$. Se realizó una comparación explícita entre el punto crítico obtenido simbólicamente y el resultado numérico para verificar la exactitud.
* **Relevancia en ML**: En escenarios reales de Machine Learning, las funciones de costo suelen ser muy complejas y no siempre es posible obtener derivadas analíticas o resolverlas simbólicamente. Los optimizadores numéricos (como los implementados en SciPy) son herramientas esenciales para encontrar los mínimos de estas funciones. Esta sección demuestra la conexión entre la teoría del cálculo (derivación simbólica) y la aplicación práctica de la optimización numérica, que es el corazón del entrenamiento de modelos de Machine Learning.

### Conclusión

Este proyecto demuestra el flujo completo desde la definición matemática de una función hasta su optimización, combinando herramientas simbólicas y numéricas en Python. Esta metodología es directamente aplicable al entendimiento y desarrollo de algoritmos de optimización en Machine Learning, donde el objetivo principal es minimizar una función de costo para encontrar los parámetros óptimos del modelo.

### Requisitos y versiones

- python 3.11.2
    - sympy 1.14.0
    - numpy 2.2.6
    - matplotlib 3.10.3
    - scipy 1.15.3

### Autor

Henzo Alejandro Arrué Muñoz

### Licencia

GPLv3