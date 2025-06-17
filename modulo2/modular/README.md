# Red Social + Benchmark BFS con Numba

Este proyecto implementa un **modelo de red social** en Python, utilizando programación orientada a objetos (POO), manejo robusto de excepciones y principios de diseño modular (SOLID). Además, compara el rendimiento de algoritmos de búsqueda en anchura (Breadth-FirstS-earch) con y sin optimización usando **Numba**.

## Descripción general

El programa tiene dos componentes principales:

### Red Social (POO)
- Modela usuarios y sus relaciones de amistad mediante clases `Usuario` y `RedSocial`.
- Permite agregar usuarios y establecer amistades, validando:
  - Que los usuarios existan.
  - Que no se agreguen usuarios duplicados.
  - Que no se repitan amistades.
  - Que no se agreguen como amigos a sí mismos.
- Genera recomendaciones de amistad mediante búsqueda en anchura (BFS) hasta un nivel de distancia 2 (amigos de amigos).

### Benchmark de BFS con Numba
- Genera un grafo simple (matriz de adyacencia) con `N` nodos conectados linealmente.
- Compara el tiempo de ejecución de:
  - Un BFS tradicional implementado en Python puro.
  - Un BFS optimizado con **Numba** (aceleración por compilación JIT).
- Visualiza los resultados en un gráfico de barras con `matplotlib`.

## Estructura

- `Usuario`: Clase que representa un usuario de la red.
- `RedSocial`: Clase que gestiona los usuarios y sus relaciones.
- `bfs_sin_numba()`: BFS sobre un grafo representado con matriz de adyacencia en Python puro.
- `bfs_con_numba()`: BFS equivalente, acelerado con Numba.
- `crear_grafo_lineal()`: Genera un grafo simple para benchmarking.
- `medir_tiempo()`: Mide el tiempo de ejecución de un algoritmo dado.
- `visualizar_tiempos()`: Dibuja un gráfico comparativo de tiempos.

## Ejecución

El programa ejecuta dos demostraciones principales:
1. **Red social:** 
   - Crea una red con usuarios de ejemplo.
   - Establece amistades.
   - Imprime recomendaciones de amistad para un usuario.

2. **Benchmark BFS:**
   - Genera un grafo de 1000 nodos.
   - Compara el tiempo de BFS con y sin Numba.
   - Muestra un gráfico de barras con los tiempos obtenidos.

## Requisitos

- Python 3.8+
  - numpy
  - matplotlib
  - numba

## Autor

Henzo Alejandro Arrué Muñoz

## Licencia

GPLv3