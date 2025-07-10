# Regresión Lineal con Álgebra Matricial

Este programa implementa una regresión lineal simple usando álgebra matricial en Python, sin librerías especializadas de machine learning. El objetivo es ilustrar cómo el modelo de regresión encuentra los parámetros que mejor ajustan una recta a un conjunto de datos con ruido gaussiano.

## Descripción

El programa:
- Genera datos sintéticos donde `y = 4 + 3x + ruido`, con `ruido` siguiendo una distribución normal estándar.
- Ajusta una línea de regresión mediante la fórmula cerrada:

  $$ \beta = (X^T X)^{-1} X^T y $$

  donde X es la matriz de diseño (con columna de unos para el término de intercepción).
- Grafica los datos y la recta ajustada sobre ellos.

## ¿Por qué álgebra matricial?

El álgebra matricial permite expresar y resolver la regresión lineal de forma compacta y eficiente:
- La solución cerrada con mínimos cuadrados ordinarios (OLS) encuentra el vector de parámetros que minimiza el error cuadrático.
- Esta técnica es la **base teórica** de muchos algoritmos en machine learning, ya que:
  - Forma el núcleo de modelos más complejos (regresión logística, redes neuronales lineales en capas, etc.).
  - Permite entender la relación entre las variables y sus predicciones de forma explícita.
  - Inspira métodos numéricos como el gradiente descendente, que generalizan la idea para problemas no lineales o de gran escala.

## Autor

Henzo Alejandro Arrué Muñoz

## Licencia

GPLv3
