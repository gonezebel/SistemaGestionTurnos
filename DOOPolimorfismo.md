# Poliformismo

El polimorfismo es el principio que permite que objetos de diferentes clases respondan de manera distinta a la misma interfaz o mensaje, manteniendo la capacidad de ser tratados de manera uniforme. Este principio establece que una misma operación puede comportarse de forma diferente según el tipo específico del objeto que la ejecute, permitiendo que el código cliente trabaje con abstracciones sin conocer los detalles específicos de cada implementación concreta.

## Relación con principios SOLID:

*Si bien la aplicación del los principios SOLID en forma concurrente genera un diseño de sistema eficiente y un estado cumplimiento general de los principios de POO, la relación principal del Poliformismo se da con los siguientes:*

+ **Open/Closed Principle (OCP):** Facilita la extensión del sistema mediante nuevas implementaciones polimórficas sin modificar el código cliente existente, ya que las nuevas clases pueden implementar las mismas interfaces y ser utilizadas de manera intercambiable.

+ **Liskov Substitution Principle (LSP):** El polimorfismo solo funciona correctamente cuando las subclases pueden sustituir completamente a sus clases base sin alterar el comportamiento esperado del sistema, siendo este principio fundamental para que el polimorfismo sea seguro y predecible.

## Relación con patrones de diseño: 

+ **Patrones Creacionales:** Por ejemplo, Template Method utiliza polimorfismo para permitir que las subclases redefinan pasos específicos de un algoritmo manteniendo la estructura general, mientras que Chain of Responsibility emplea polimorfismo para que diferentes manejadores procesen solicitudes según su capacidad específica de manejo.

+ **Patrones Estructurales:** En relación a estructurales, Visitor utiliza polimorfismo donde tanto el visitante como el elemento visitado determinan qué método específico se ejecuta, mientras que Flyweight emplea polimorfismo para que diferentes objetos flyweight compartan comportamientos comunes pero mantengan estados intrínsecos específicos.

+ **Patrones de Comportamiento:** Respecto a los de tipo de comportamiento, Template Method define un esqueleto algorítmico en la clase base donde los métodos polimórficos de las subclases proporcionan implementaciones específicas, mientras que Chain of Responsibility utiliza polimorfismo para que cada eslabón de la cadena decida si puede manejar una solicitud o debe pasarla al siguiente eslabón.

## Ejemplo en el proyecto

En el sistema de turnos médicos, el polimorfismo se manifiesta en la jerarquía de profesionales médicos: las clases MedicoClinico, Radiologo y Fisioterapeuta que heredan de Profesional representan un ejemplo perfecto de polimorfismo donde cada especialidad puede responder de manera específica a operaciones médicas comunes. De esta forma, no solo se permite flexibilidad en el diseño, sino que se facilita la extensibilidad y mantenibilidad del código al proporcionar mecanismos para tratar objetos diversos de manera uniforme mientras respetan sus comportamientos específicos.


