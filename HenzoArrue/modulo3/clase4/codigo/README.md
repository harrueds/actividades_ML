# Optimización y Análisis Geométrico de Funciones en Dos Variables

## 1. Introducción

Este proyecto implementa herramientas del cálculo diferencial multivariable para el estudio analítico y gráfico de funciones en dos variables. Se aborda el cálculo simbólico de derivadas, la obtención del gradiente y la matriz Hessiana, la identificación y clasificación de puntos críticos, y la visualización detallada mediante gráficos 2D y 3D. Además, se vinculan estos conceptos con su aplicación práctica en Machine Learning, especialmente en algoritmos de optimización.

## 2. Metodología

El análisis se llevó a cabo mediante los siguientes pasos:

### a. Definición de la función:
Se definió simbólicamente la función $g(x, y) = x^2 + 3y^2 - 4x + 2y + 1$ utilizando la librería `SymPy`.

### b. Cálculo simbólico:
- Se obtuvieron las derivadas parciales $\frac{\partial g}{\partial x}$ y $\frac{\partial g}{\partial y}$.
- Se construyó el vector gradiente $\nabla g(x, y)$.
- Se generó la matriz Hessiana $H_g(x, y)$, compuesta por segundas derivadas parciales.

### c. Identificación y clasificación del punto crítico:
- Se resolvió el sistema $\nabla g(x, y) = \vec{0}$ para encontrar los puntos críticos.
- La matriz Hessiana fue evaluada en dichos puntos.
- A partir de los valores propios de la Hessiana, se determinó si el punto crítico correspondía a un mínimo local, máximo local o punto de silla.

### d. Visualización gráfica:
- La función simbólica $g(x, y)$ y sus derivadas se transformaron a funciones numéricas utilizando `sp.lambdify`, con backend `"numpy"`.
- Se generó un `meshgrid` en el dominio $x, y \in [-5, 5]$.
- Se graficó la superficie 3D de la función y su correspondiente mapa de contorno, destacando el punto crítico con su clasificación.
- Las expresiones simbólicas se presentaron mediante `display(Math(...))` para lograr una salida clara en formato LaTeX.

## 3. Visualización gráfica:
   * La función simbólica $g(x, y)$ y sus derivadas fueron convertidas a funciones numéricas utilizando `sp.lambdify`, con backend `"numpy"`.
   * Se generó un `meshgrid` de valores en el rango $x, y \in [-5, 5]$.
   * Se graficó la superficie 3D de la función y un mapa de contorno (contour plot), marcando el punto crítico con su respectiva clasificación.
   * Ambas gráficas incluyen líneas de grilla que permiten observar con mayor claridad la geometría de la función en los ejes coordenados y obtener una aproximación visual a los valores.
   * Las expresiones matemáticas simbólicas fueron presentadas con `display(Math(...))` para lograr una salida clara y en formato LaTeX.

## 4. Relevancia en Machine Learning

La comprensión del gradiente, los puntos críticos y la curvatura de funciones es fundamental para el diseño de algoritmos de aprendizaje automático.

### Descenso de Gradiente:
  El gradiente proporciona la dirección de máximo incremento. El descenso de gradiente lo utiliza en dirección opuesta para minimizar funciones de costo en modelos de Machine Learning. Este principio guía la actualización iterativa de parámetros para mejorar el rendimiento del modelo.

### Análisis de la Hessiana:
  La matriz Hessiana permite evaluar la naturaleza del punto crítico (mínimo, máximo o punto de silla). Esta clasificación es crucial para evitar estancamientos en mínimos locales poco útiles o puntos de silla inestables, y así garantizar una convergencia más efectiva hacia soluciones óptimas.

Este proyecto ilustra cómo los fundamentos matemáticos del cálculo diferencial permiten comprender mejor los mecanismos internos de los algoritmos de aprendizaje y optimización, facilitando su aplicación rigurosa en contextos reales.

## Aplicación en Machine Learning

La comprensión del gradiente, los puntos críticos y la curvatura de funciones es fundamental para el diseño de algoritmos de aprendizaje automático.

### • Descenso de Gradiente:

El gradiente indica la dirección de mayor incremento. El descenso de gradiente utiliza la dirección opuesta para minimizar funciones de costo, lo cual es esencial en el entrenamiento de modelos de Machine Learning.

### • Análisis de la Hessiana:

La matriz Hessiana proporciona información sobre la curvatura local de la función. Clasificar los puntos críticos evita que los algoritmos queden atrapados en mínimos locales subóptimos o puntos de silla inestables, mejorando así la convergencia hacia soluciones óptimas.

Este proyecto muestra cómo los fundamentos matemáticos del cálculo diferencial pueden usarse para comprender y mejorar algoritmos de optimización en contextos reales.

### Requisitos

- Python 3.8 o superior  
- Librerías:
   - sympy
   - numpy
   - matplotlib
   - IPython (para mostrar salidas en LaTeX)

### Autor

Henzo Alejandro Arrué Muñoz

### Licencia

GPLv3
