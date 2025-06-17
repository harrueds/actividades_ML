# Sistema de Gestión de Vehículos en Python (POO)

## Descripción

Este proyecto consiste en el desarrollo de un sistema de gestión de vehículos utilizando Programación Orientada a Objetos (POO) en Python. El código se encuentra implementado dentro de un Jupyter Notebook y tiene como objetivo demostrar el uso práctico de los principios de diseño SOLID, en particular:

- **SRP (Single Responsibility Principle)**: Principio de Responsabilidad Única.
- **OCP (Open/Closed Principle)**: Principio Abierto/Cerrado.

El sistema permite registrar distintos tipos de vehículos (como autos y motos), simular su comportamiento y aplicar principios de diseño que favorecen la mantenibilidad y extensibilidad del código.


## Estructura del Proyecto

- `henzo_arrue_act3_m2.ipynb`: contiene todo el código del sistema, implementación de clases y pruebas.
- `README.md`: documento explicativo del proyecto, estructura y principios aplicados.


## Componentes del Sistema

### Clase `Vehiculo`

Esta es la clase base del sistema. Define los atributos comunes a todos los vehículos: marca, modelo y año. Además, contiene métodos genéricos como `acelerar` y `obtener_info`.

**Responsabilidad única (SRP):** representar un vehículo genérico.

**Extensible (OCP):** las subclases pueden sobrescribir los métodos sin modificar la clase original.


### Subclase `Auto`

Hereda de `Vehiculo` y sobrescribe el método `acelerar` con un comportamiento propio. Además, incorpora un método exclusivo llamado `abrir_maletero`.

**SRP:** encapsula todo lo necesario para representar un auto.

**OCP:** se puede crear la clase sin modificar `Vehiculo`.


### Subclase `Moto`

También hereda de `Vehiculo` y sobrescribe el método `acelerar` con su propio mensaje distintivo. Agrega un método nuevo llamado `hacer_caballito`, propio de las motos.

**SRP:** encapsula el comportamiento único de una motocicleta.

**OCP:** amplía el sistema sin tocar la clase base ni otras subclases.


### Lógica de Prueba

En el notebook se crean instancias de las distintas clases (`Auto` y `Moto`) y se ejecutan sus métodos para demostrar cómo funciona el polimorfismo. También se comprueba el comportamiento específico de cada tipo de vehículo mediante llamadas condicionales a sus métodos particulares.


## Principios SOLID Aplicados

### SRP – Single Responsibility Principle

Cada clase en el sistema tiene **una sola responsabilidad bien definida**:

- `Vehiculo` solo define atributos y métodos comunes.
- `Auto` y `Moto` solo se encargan de comportamientos particulares de esos tipos de vehículos.
- No se mezclan funcionalidades entre clases.

### OCP – Open/Closed Principle

El sistema está diseñado para ser **extensible sin necesidad de modificar las clases existentes**:

- Nuevos tipos de vehículos pueden agregarse como nuevas subclases.
- El código que usa las clases (como los bloques de prueba) funciona con cualquier objeto que herede de `Vehiculo`, gracias al uso de polimorfismo.


## Cómo Ejecutar

1. Abrir el archivo `henzo_arrue_act3_m2.ipynb` en la plataforma adecuada (VSCodium, VS Code, Jupyter Notebook, Google Colab, etc.).
2. Ejecutar las celdas paso a paso para visualizar el funcionamiento del sistema.


## Autor

Henzo Alejandro Arrué Muñoz

## Licencia

GPLv3