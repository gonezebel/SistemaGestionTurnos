# Principio de Inversión de Dependencias (DIP) 

El principio DIP establece que los módulos de alto nivel no deben depender de módulos de bajo nivel, sino que ambos deben depender de abstracciones. Mediante este principio, se ocultan los detalles de implementación, ganando flexibilidad ante cambios.

## Motivación 

En el sistema de gestión de turnos, por ejemplo, si el componente de gestión de turnos dependiera directamente de una implementación específica de notificación (como Whatsapp, SMS, o email), cualquier cambio en el sistema de notificaciones requeriría modificar el gestor de turnos. Este acoplamiento directo dificulta:

* Realizar pruebas unitarias aisladas: Cambiar entre diferentes implementaciones (por ejemplo, pasar de notificaciones por email a notificaciones por app).
* Mantener y evolucionar el sistema de forma independiente.

El diseño original sufría de rigidez debido a que el gestor de turnos dependía directamente de implementaciones específicas de notificación. Aplicando el principio DIP, se introdujo la interfaz IServicioNotificacion como abstracción intermedia, permitiendo que el gestor de turnos trabaje con cualquier implementación de notificación (Email, SMS, WhatsApp) sin conocer sus detalles internos, lo que facilita la adaptación a nuevos requisitos y la implementación de pruebas sin modificar componentes existentes.

## Estructura de Clases 
 * [Link drawio](https://drive.google.com/file/d/1wYh8ik2u8-rpyEPE5HFxtHsch7Rd-3iY/view?usp=sharing)
 ![Ejemplo ISP](imagenes/022_Parcial_1_SOLID_DIP.jpg)

