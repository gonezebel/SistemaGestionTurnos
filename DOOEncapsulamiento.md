# Encapsulamiento 

El encapsulamiento es el principio de la POO que busca ocultar los detalles internos de implementación de un objeto, exponiendo únicamente una interfaz pública controlada que permita interactuar con el objeto de manera segura y coherente. Se materializa a través de modificadores de visibilidad que definen quién puede acceder a cada elemento de la clase: Los modificadores private ocultan completamente los atributos del acceso externo, protected permite acceso a subclases y clases del mismo paquete, mientras que public expone elementos que forman parte de la interfaz pública del objeto.

## Relación con principios SOLID:

*Si bien la aplicación del los principios SOLID en forma concurrente genera un diseño de sistema eficiente y un estado cumplimiento general de los principios de POO, la relación principal de la Abstracción se da con los siguientes:*

+ **Single Responsibility Principle (SRP)**: El encapsulamiento es el mecanismo que materializa el SRP al agrupar naturalmente datos y métodos que están relacionados y cambian por las mismas razones dentro de una sola unidad cohesiva. Al encapsular elementos en una clase, automáticamente se define una responsabilidad específica porque todos los elementos encapsulados juntos tienen una razón común de existir y cambiar, evitando que responsabilidades se dispersen por múltiples clases y dando seguridad de que cada clase tenga una sola razón para ser modificada.
