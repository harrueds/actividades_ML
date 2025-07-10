# Optimización de un Modelo de Regresión Lineal Simple

## Descripción General

Este proyecto implementa una solución completa en Python para entrenar un modelo de **regresión lineal simple** a partir de datos sintéticos. Se abordan dos métodos fundamentales para estimar los parámetros óptimos del modelo:

- **Cálculo cerrado** mediante la **fórmula normal**.
- **Optimización iterativa** utilizando el **descenso de gradiente**.

Incluye validación de datos, manejo de errores personalizados, visualización de los modelos y evolución del error, además de una comparación entre ambos enfoques.

## Objetivos

- Generar datos sintéticos reproducibles.
- Implementar el modelo de regresión lineal mediante dos métodos.
- Calcular y graficar la función de costo.
- Visualizar comparativamente ambos modelos.
- Aplicar manejo robusto de excepciones.
- Evaluar rendimiento y precisión.

## Módulos y Funcionalidades

### 1. Generación de Datos
- Modelo:  
  **𝑦 = 4 + 3𝑥 + ε**  
  con ε = ruido gaussiano.
- Generación de 100 puntos usando `NumPy`.
- Validaciones sobre cantidad de muestras, rango y desviación estándar del ruido.
- Datos reproducibles mediante semilla (`np.random.seed`).
- Inclusión del término de sesgo (columna de unos en X).

### 2. Cálculo Cerrado (Ecuación Normal)
- Implementación de:  
  **𝛽 = (XᵀX)⁻¹Xᵀy**
- Cálculo de parámetros óptimos `θ₀` y `θ₁`.
- Manejo de errores si la matriz es singular (no invertible).
- Validación del formato y dimensión de los datos.

### 3. Descenso de Gradiente
- Derivación del gradiente del MSE.
- Algoritmo iterativo con tasa de aprendizaje y número de iteraciones configurables.
- Inicialización de parámetros en cero.
- Cálculo y registro del costo (`MSE`) en cada iteración.
- Validaciones y manejo de errores.

### 4. Visualización
- Gráfico comparativo:  
  - Datos reales  
  - Recta obtenida por fórmula cerrada  
  - Recta obtenida por descenso de gradiente  
- Curva de evolución del costo a lo largo de las iteraciones.

### 5. Manejo de Excepciones
- Se define la clase `ErrorFormatoDatosInvalido`.
- Uso extensivo de bloques `try-except` para controlar errores comunes y críticos.
- Mensajes informativos para facilitar la depuración.

## Resultados Esperados

| Método              | Parámetros (θ₀, θ₁)       | Costo Final (MSE) |
|------------------------|----------------------------|-------------------|
| Cálculo Cerrado     | `[β₀, β₁]`                 | `≈ XX.XXXX`       |
| Descenso Gradiente  | `[θ₀, θ₁]`                 | `≈ XX.XXXX`       |

> **Nota**: El costo puede variar levemente según el ruido generado aleatoriamente.

## Complejidad y Elección del Método

| Método              | Complejidad Big O         | Ventajas                                 |
|---------------------|----------------------------|------------------------------------------|
| Cálculo Cerrado     | O(n³)                      | Preciso, rápido con pocos datos          |
| Descenso Gradiente  | O(n·i), i = iteraciones    | Escalable, ideal para grandes datasets   |

### Elección sugerida:
- **Problemas pequeños o análisis offline** → **Cálculo Cerrado**
- **Datos masivos o transmisión continua** → **Descenso de Gradiente**

## Evidencias

El proyecto genera:
- Visualización de los modelos ajustados.
- Gráfico de la evolución del error (función de costo).
- Impresiones en consola de los parámetros y costos finales.
- Mensajes de error controlados y explícitos.

## Requisitos

- Python 3.11.2
  - numpy
  - matplotlib

## Autor

Henzo Alejandro Arrué Muñoz

## Licencia

GPLv3
