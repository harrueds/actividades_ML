# Optimización de Código en Python

## Estructura del código

1. `suma_productos_bucle`: cálculo de la suma de productos usando bucles tradicionales de Python.
2. `suma_productos_numpy`: versión optimizada utilizando operaciones vectorizadas con NumPy.
3. `suma_productos_numba`: versión acelerada usando el decorador `@jit` de Numba.
4. `medir_tiempo`: context manager personalizado para medir el tiempo de ejecución de bloques de código.


## Resultados de rendimiento (promedios en 15 ejecuciones)

| Método         | Tiempo (segundos) |
|----------------|-------------------|
| Bucles nativos | 0.298             |
| NumPy          | 0.078             |
| Numba          | 0.894             |


## Interpretación de los resultados

- **NumPy fue el más eficiente**, gracias a su motor interno optimizado en C, ideal para este tipo de operaciones vectorizadas.
- **La versión con bucles nativos** es significativamente más lenta, lo cual era esperado al no contar con optimizaciones a bajo nivel.
- **Numba fue más lenta que NumPy e incluso que los bucles**, debido a que:
  - La compilación JIT genera una sobrecarga adicional.
  - La arquitectura del sistema y del CPU no optimiza adecuadamente este tipo de función.
  - El entorno Jupyter (Notebook en VSCodium) puede afectar el rendimiento de Numba.
  - La función, al no ser lo suficientemente intensiva, no justifica el uso del compilador JIT en este caso.


## Justificación de la elección de cada técnica de optimización aplicada

1. **Bucles nativos**  
   Se usaron como línea base para comparar las optimizaciones. Representan la forma más simple y directa de resolver el problema en Python.

2. **Vectorización con NumPy**  
   Se eligió NumPy porque permite realizar operaciones en arreglos de forma eficiente, eliminando bucles y delegando los cálculos a funciones internas en C, altamente optimizadas. Su rendimiento fue el mejor en esta prueba.

3. **Aceleración con Numba (@jit)**  
   Se aplicó Numba para explorar la aceleración por compilación JIT. Sin embargo, en este caso particular no superó a NumPy por las condiciones del entorno y la baja intensidad de la función. Esta situación demuestra que Numba **no siempre es la mejor opción** si la función es simple o el sistema no tiene recursos compatibles.

4. **Context Manager personalizado**  
   Se implementó para mejorar la claridad y control al medir tiempos de ejecución. Facilita la evaluación de bloques de código sin repetir lógica.


## Capturas requeridas

- Código abierto en el editor (VSCodium).
- Salida en la terminal o Notebook mostrando los tiempos medidos.
- Las capturas se incluyen en la carpeta.

## Instrucciones de ejecución

Este proyecto puede ejecutarse en cualquier entorno Python 3. Se recomienda instalar las dependencias con:

pip install numpy numba

## Autor
- Henzo Alejandro Arrué Muñoz

## Licencia
- GPLv3
