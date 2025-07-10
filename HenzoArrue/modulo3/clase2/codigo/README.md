# Resolución de Sistemas de Ecuaciones y Transformaciones Lineales en 2D

## Descripción del proyecto

Este proyecto está dividido en dos partes:

1. **Resolución de sistemas de ecuaciones lineales**
Usando álgebra matricial con `numpy`, utilizando funciones como `np.linalg.solve` para sistemas determinados y `np.linalg.lstsq` para sistemas sobre- o sub-determinados.

2. **Modelado y visualización de transformaciones lineales en 2D**
Aplicando una transformación compuesta (rotación + escalado) sobre un conjunto de puntos y mostrando gráficamente el efecto de dicha transformación.

## Estructura

- **Código Python** 
  - Resuelve el sistema `Ax = b`.
  - Construye las matrices de rotación y escalado.
  - Aplica la transformación sobre puntos dados.
  - Visualiza los resultados con `matplotlib`.

## Decisiones de diseño

- Se usó `np.radians(45)` para convertir el ángulo a radianes, facilitando la construcción de la matriz de rotación.
- Se definió la matriz compuesta como `T = S @ R`, siguiendo el orden lógico de aplicar primero la rotación y luego el escalado.
- Se conectan los puntos originales con los transformados en la visualización para facilitar la interpretación.

## Requisitos

- python 3.11.2
  - numpy 2.2.6
  - matplotlib 3.10.3

## Autor

Henzo Alejandro Arrué Muñoz

## Licencia

GPLv3
