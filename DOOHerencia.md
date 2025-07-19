# Herencia

La herencia es el principio de la POO que permite que una subclase o clase derivada adquiera automáticamente los atributos y métodos de otra clase superclase o clase base superior, estableciendo una relación jerárquica que refleja conceptos de especialización y generalización del mundo real. Este principio facilita la reutilización de código al permitir que las clases compartan características comunes mientras desarrollan funcionalidades específicas.

## Relación con los Principios SOLID

*Si bien la aplicación del los principios SOLID en forma concurrente genera un diseño de sistema eficiente y un estado cumplimiento general de los principios de POO, la relación principal de la Herencia se da con los siguientes:*

+ **Liskov Substitution Principle (LSP):** La herencia es el mecanismo principal que hace posible la sustitución de Liskov, ya que las subclases deben poder reemplazar a sus superclases sin alterar el comportamiento esperado del sistema, siendo fundamental que las clases derivadas respeten los contratos establecidos por sus clases base.

+ **Open/Closed Principle (OCP):** Facilita la extensión del sistema mediante la creación de nuevas subclases que agregan funcionalidad sin modificar las clases base existentes, permitiendo que el código sea abierto para extensión pero cerrado para modificación al heredar comportamientos base y especializarlos.

+ **Dependency Inversion Principle (DIP)**: Permite que el código cliente dependa de clases base abstractas o interfaces mientras trabaja con implementaciones específicas de las subclases, facilitando la inversión de dependencias al hacer que módulos de alto nivel dependan de abstracciones que las subclases implementan.

## 



