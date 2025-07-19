#  Abstracción

En el diseño orientado a objetos, la abstracción es el proceso mediante el cual se identifican y modelan únicamente los aspectos esenciales de un objeto o concepto del mundo real, ocultando los detalles innecesarios o irrelevantes para el contexto específico del sistema a diseñar, facilitando la comprensión y el diseño del código.

## Relación con principios SOLID:

+ **Single Responsibility Principle (SRP)**: La abstracción ayuda a definir responsabilidades claras y únicas para cada clase. Al abstraer solo los aspectos esenciales de una entidad, naturalmente se delimita su responsabilidad principal, evitando la sobrecarga de funcionalidades no relacionadas.

+ **Open/Closed Principle (OCP)**: Las abstracciones colaboran a que el código sea abierto para extensión pero cerrado para modificación. Las interfaces y clases abstractas proporcionan puntos de extensión estables que permiten agregar nuevas funcionalidades sin alterar el código existente.

+ **Liskov Substitution Principle (LSP)**: La abstracción correcta colabora a que las implementaciones derivadas puedan sustituir a sus abstracciones base sin afectar el comportamiento del sistema. 

+ **Interface Segregation Principle (ISP)**: La abstracción promueve la creación de interfaces específicas y cohesivas en lugar de interfaces inamovibles. Esto evita que las clases dependan de métodos que no utilizan.

+ **Dependency Inversion Principle (DIP)**: La abstracción es fundamental para la inversión de dependencias, ya que permite que los módulos de alto nivel dependan de abstracciones (interfaces) en lugar de implementaciones concretas.

## Relación con patrones de diseño: 

+ **Patrones Creacionales**: Por ejemplo, lo patrones Factory Method y Abstract Factory, utilizan abstracciones para simplificar la de creación de objetos. Factory lo implementa a traves de una superclase, delegando a las subclases la decisión de qué clase concreta instanciar; mientras que que Abstract extiende la abstracción para crear familias completas de objetos relacionados sin especificar clase concreta.

+ **Patrones Estructurales**: En primer lugar, el patrón Bridge, utiliza la abstracción para separar completamente "qué hace un objeto" de "cómo lo hace". Crea dos jerarquías independientes: una abstracción que define las operaciones de alto nivel que ve el cliente, y una implementación que define las operaciones que ejecutan. Esto permite que ambas jerarquías evolucionen independientemente.

Por otro lado, patrones como Adapter y Decorator, emplean abstracciones para definir interfaces comunes que permiten la interoperabilidad entre componentes incompatibles en el primero o la extensión transparente de funcionalidades en el segundo.

    * En Adapter, la abstracción es esencial para hacer compatible sistemas con interfaces incompatibles. El adaptador implementa la interfaz abstracta esperada por el cliente mientras internamente traduce las llamadas a la interfaz del sistema adaptado. Esta abstracción oculta la incompatibilidad y permite tratar sistemas heterogéneos de manera uniforme.

    * En cuanto a Decorator, la abstracción permite que tanto el objeto original como todos los "añadidos" (decoradores) se vean iguales desde afuera, permitiendo añadir capas de funcionalidades sin afectar las anteriores porque cada nueva capa puede tratar a lo que está debajo como si fuera el objeto original porque todos usan la misma abstracción para comunicarse.

+ **Patrones de Comportamiento**: Patrones como Strategy y State utilizan abstracciones para encapsular algoritmos y comportamientos variables, permitiendo su intercambio dinámico sin afectar el contexto.

    * En Strategy, por ejemplo, se define una abstracción común para una familia de algoritmos intercambiables. Esta  abstracción separa la interfaz del algoritmo de su implementación, permitiendo agregar nuevos algoritmos en forma modular simplificada.

    * Respecto a State, la abstracción define operaciones comunes que todos los estados deben implementar. Cada estado concreto maneja estas operaciones según su lógica específica, mientras que el contexto delega comportamientos a través de la abstracción. Esto permite que el objeto cambie de comportamiento dinámicamente manteniendo una interfaz consistente.

