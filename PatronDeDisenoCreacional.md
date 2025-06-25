# Anexo - Aplicación de Patrón de Diseño creacional - FACTORY METHOD

Los patrones de diseño creacionales proporcionan diversos mecanismos de creación de objetos que incrementan la flexibilidad y la reutilización del código existente. Estos patrones se enfocan en el proceso de creación de objetos, encapsulando el conocimiento sobre qué clases concretas utiliza el sistema y ocultando cómo se crean e inicializan estas instancias.

### Relación con principios SOLID:

+ SRP (Single Responsibility Principle): Separan la responsabilidad de crear objetos de su uso.
+ OCP (Open/Closed Principle): Facilitan la extensión del sistema con nuevos tipos sin modificar código existente.
+ DIP (Dependency Inversion Principle): Permiten depender de abstracciones en lugar de implementaciones concretas.

### Propósito y Tipo del Patrón

Factory Method es un patrón de diseño creacional que proporciona una interfaz para crear objetos en una superclase, pero permite a las subclases alterar el tipo de objetos que se crearán.

### Problema resuelto

El sistema de gestión de turnos necesita enviar notificaciones automáticas por diferentes medios, email y SMS según el enunciado, cuando ocurren eventos como confirmación, cancelación o modificación de turnos. El desafío es crear un sistema extensible que permita agregar nuevos tipos de notificación sin modificar el código existente, por ejemplo a través de Whatsapp.

### Solución

El patrón Factory Method permite crear diferentes tipos de notificaciones a través de una interfaz común, delegando a las subclases la decisión de qué clase concreta instanciar. Esto hace el sistema flexible y extensible.

## Motivación

### Problema detallado
El centro de salud necesita digitalizar su sistema de turnos que actualmente maneja en agenda física, lo que genera problemas como pérdida de citas, falta de confirmación y superposición de turnos. Parte de los problemas, radica en la fase de comunicación donde el desafío técnico implica que las notificaciones deben enviarse por múltiples canales (email, SMS) y el sistema debe ser extensible para incorporar futuros medios de comunicación como Whatsapp, Telegram o notificaciones push, sin requerir modificaciones al código base.

#### Clases del problema original:

+ **GestorTurnos:** Maneja la lógica de negocio de los turnos
+ **Turno:** Entidad que representa un turno médico
+ **Paciente y Profesional:** Entidades que necesitan recibir notificaciones

##### Limitaciones del enfoque original:
Sin el patrón, el GestorTurnos tendría que conocer todos los tipos de notificación y contener lógica condicional para decidir cómo enviar cada tipo de mensaje, violando el principio de responsabilidad única y el principio abierto/cerrado.

#### Nuevas clases incorporadas con Factory Method:

+ **Notificacion (Clase abstracta)**
 ! **Función:** Define la interfaz común para crear notificaciones
 ! Método clave: crearNotificacion() - método factory que las subclases deben implementar
 ! Responsabilidad: Encapsula la lógica común de envío de notificaciones

+ EmailNotification
 ++ Función: Factory concreto para crear notificaciones por email
 ++ Responsabilidad: Configura parámetros SMTP, valida direcciones de email, crea objetos EmailNotificacion

+ WhatsAppNotification
++ Función: Factory concreto para crear notificaciones por WhatsApp
++ Responsabilidad: Gestiona API de WhatsApp, valida números de teléfono, crea objetos WhatsAppNotificacion

+ SMSNotification
++ Función: Factory concreto para crear notificaciones por SMS
++ Responsabilidad: Integra con proveedor SMS, valida números internacionales, crea objetos SMSNotificacion

+ Notificacion (Interfaz)
++Función: Define el contrato común para todas las notificaciones
++Métodos: configurar(), enviar(), validarDatos()

+ GestorNotificaciones
++ Función: Cliente que utiliza las factories sin conocer implementaciones específicas
++ Responsabilidad: Coordina el envío de notificaciones usando el factory apropiado según el tipo requerido

#### Ventajas de la nueva estructura:

+ Extensibilidad: Agregar una nueva NotificacionTelegramFactory solo requiere crear dos nuevas clases sin modificar código existente
+ Mantenibilidad: Cada tipo de notificación está encapsulado en su propia factory
+ Testabilidad: Es fácil crear factories mock para testing
+ Flexibilidad: El sistema puede decidir en tiempo de ejecución qué tipo de notificación usar
+ Cumplimiento SOLID: Respeta SRP (cada factory tiene una responsabilidad), OCP (abierto para extensión, cerrado para modificación) y DIP (depende de abstracciones)

## Estructura de clases



