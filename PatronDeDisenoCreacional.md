# Anexo - Aplicación de Patrón de Diseño creacional - FACTORY METHOD

Los patrones de diseño creacionales proporcionan diversos mecanismos de creación de objetos que incrementan la flexibilidad y la reutilización del código existente. Estos patrones se enfocan en el proceso de creación de objetos, encapsulando el conocimiento sobre qué clases concretas utiliza el sistema y ocultando cómo se crean e inicializan estas instancias.

### Relación con principios SOLID:

+ SRP (Single Responsibility Principle): Separan la responsabilidad de crear objetos de su uso.
+ OCP (Open/Closed Principle): Facilitan la extensión del sistema con nuevos tipos sin modificar código existente.
+ DIP (Dependency Inversion Principle): Permiten depender de abstracciones en lugar de implementaciones concretas.

## Motivación

### Propósito y Tipo del Patrón

Factory Method es un patrón de diseño creacional que proporciona una interfaz para crear objetos en una superclase, pero permite a las subclases alterar el tipo de objetos que se crearán.

### Problema resuelto

El sistema de gestión de turnos necesita enviar notificaciones automáticas por diferentes medios, email y SMS según el enunciado, cuando ocurren eventos como confirmación, cancelación o modificación de turnos. El desafío es crear un sistema extensible que permita agregar nuevos tipos de notificación sin modificar el código existente, por ejemplo a través de Whatsapp.

### Solución

El patrón Factory Method permite crear diferentes tipos de notificaciones a través de una interfaz común, delegando a las subclases la decisión de qué clase concreta instanciar. Esto hace el sistema flexible y extensible.

