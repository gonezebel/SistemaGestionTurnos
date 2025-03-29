# Anexo 1 - Introducción al Diseño Orientado a Objetos

## Concepto del Paradigma Orientado a Objetos

La programación orientada a objetos (en adelante POO) es un enfoque conceptual específico para diseñar programas. Este paradigma se concentra en el objeto como lo percibe el usuario, partiendo de la abstracción de entidades del mundo real como objetos, que tienen datos y comportamientos aosciados. 

Lo distintivo de la POO es la técnica de poner todos los atributos y métodos de un objeto en una estructura independiente, la propia clase. En otras palabras, sos objetos son son las "cosas" relevantes para el sistema bajo análisis, mientras que las clases son agrupaciones de objetos que son óptimas para reutilizarse y darles mantenimiento. Una clase define el conjunto de atributos y comportamientos compartidos por cada objeto de la clase. Los programadores deben definir las diversas clases en el programa que escriben, y cuando el programa se ejecuta, los objetos se pueden crear a partir de la clase establecida.

**Diferencias entre la POO y el paradigma de programación estructural**

i. Organización sistémica: El paradigma estructurado se basa en la división del programa en procedimientos y funciones independientes, con tareas específicas, mientras que la POO se organiza en torno a objetos que son instancias de clases que encapsulan datos y comportamientos relacionados. 

ii. Diseño: Mientras que el modelo estructurado se centra en la descomposición del sistema en funciones y procedimientos, la POO parte de la encapsulación de datos y comportamiento. Por otra parte, al crear objetos que contienen datos y código de programación, un cambio en un objeto tiene un impacto mínimo en otros objetos, lo que mejora el mantenimiento, asi como permite la reusabilidad de objetos, reduciendo los costos de desarrollo en sistemas computacionales.

## Los cuatro fundamentos de POO

 **I. Encapsulación:** Ocultamiento de de detalles internos del objeto, exponiendo solo sus interfaces públicas, favoreciendo, así, la modularidad y la seguridad del sistema.

 EJ: El control remoto es un objeto que encapsula toda su complejidad interna (circuitos, baterías, sensores infrarrojos) detrás de una interfaz simple (los botones).

 ![Ejemplo encapsulación](imagenes/00_diagrama_encapsulamiento.jpg)

 **II. Abstracción:**  Simplificar la complejidad de los objetos reales modelando solo los aspectos esenciales relevantes para el sistema.

 EJ: El la utilización de un cajero automático por parte de un usuario. La máquina presenta solo funciones simples al usuario (retirar dinero, consultar saldo, transferir) mientras oculta toda la complejidad subyacente. El usuario no necesita entender los sistemas de autenticación, las consultas a bases de datos, los protocolos de comunicación interbancaria o los mecanismos de seguridad que operan tras cada botón que presiona.
 
 ![Ejemplo abstracción](imagenes/01_diagrama_abstracción.jpg)

 **III. Herencia: ** Permite que un objeto obtenga propiedades y comportamientos de otro objeto, a través de una jerarquía de clases, permitiendo la reutilización del código.

 EJ: Los vehículos de transporte automotor representan un ejemplo herencia. Todos los vehículos comparten características comunes (motocicletas, automóviles, camiones, etc), pero cada tipo específico tiene sus propias peculiaridades.

  ![Ejemplo herencia](imagenes/01_diagrama_abstracción.jpg)


 **IV. Poliformismo: **: 
 
