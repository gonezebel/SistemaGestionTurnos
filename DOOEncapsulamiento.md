# Encapsulamiento 

El encapsulamiento es el principio de la POO que busca ocultar los detalles internos de implementación de un objeto, exponiendo únicamente una interfaz pública controlada que permita interactuar con el objeto de manera segura y coherente. Se materializa a través de modificadores de visibilidad que definen quién puede acceder a cada elemento de la clase: Los modificadores private ocultan completamente los atributos del acceso externo, protected permite acceso a subclases y clases del mismo paquete, mientras que public expone elementos que forman parte de la interfaz pública del objeto.

## Relación con principios SOLID:

*Si bien la aplicación del los principios SOLID en forma concurrente genera un diseño de sistema eficiente y un estado cumplimiento general de los principios de POO, la relación principal del Encapsulamiento se da con los siguientes:*

+ **Interface Segregation Principle (ISP)**: El encapsulamiento implementa directamente el ISP mediante los modificadores de visibilidad que controlan exactamente qué métodos y datos son accesibles desde el exterior, permitiendo crear interfaces públicas específicas y enfocadas para diferentes tipos de clientes. Al marcar elementos como privados, protegidos o públicos, el encapsulamiento evita que las clases cliente dependan de funcionalidades internas que no necesitan, exponiendo solo los métodos relevantes para cada uso específico y segregando automáticamente las interfaces según las necesidades de cada cliente.

+ **Open/Closed Principle (OCP):** El encapsulamiento facilita el OCP al ocultar los detalles de implementación interna detrás de una interfaz pública estable, permitiendo que la implementación interna de una clase sea modificada sin afectar el código cliente que depende únicamente de los métodos públicos. Esta separación entre interfaz pública (cerrada para modificación) e implementación privada (abierta para modificación interna) hace posible que las clases evolucionen internamente sin romper el contrato público establecido por la clase base.
