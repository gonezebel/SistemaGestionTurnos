# Anexo - Aplicación de patrón de diseño de comportamiento - State

Los patrones de diseño de comportamiento se ocupan de algoritmos y la asignación de responsabilidades entre objetos. Estos patrones definen cómo los objetos se comunican entre sí y el modo en que se distribuyen las responsabilidades, centrándose en los patrones de comunicación entre objetos y en el flujo de control en un programa.

### Relación con principios SOLID:

+ **SRP (Single Responsibility Principle):** Cada estado tiene una responsabilidad específica y bien definida
+ **OCP (Open/Closed Principle):** Facilita agregar nuevos estados sin modificar estados existentes
+ **LSP (Liskov Substitution Principle):** Los estados concretos pueden sustituir al estado base sin afectar el funcionamiento
+ **DIP (Dependency Inversion Principle):** El contexto depende de la abstracción del estado, no de implementaciones concretas

### Propósito y tipo del patrón

State es un patrón de diseño de comportamiento que permite a un objeto alterar su comportamiento cuando su estado interno cambia. Aparece como si el objeto hubiera cambiado de clase.

### Problema resuelto

Los turnos médicos en el centro de salud pasan por diferentes estados (Solicitado, Confirmado, En Curso, Finalizado, Cancelado) y cada estado tiene comportamientos específicos y transiciones válidas. Sin este patrón, el código tendría condicionales masivos para manejar cada estado.

### Solución

El patrón State encapsula los comportamientos específicos de cada estado en clases separadas y permite que el turno delegue el trabajo al objeto de estado actual, facilitando las transiciones y manteniendo el código limpio.

## Motivación

### Problema detallado

El requerimiento del sistema indica que éste debe llevar un registro del historial de turnos de cada paciente y gestionar diferentes estados como confirmado, cancelado, pendiente. El problema es que cada estado de un turno tiene comportamientos específicos y transiciones válidas:

+ **Estado Solicitado:** Puede confirmarse o cancelarse, pero no puede finalizarse
+ **Estado Confirmado:** Puede cancelarse o iniciarse (pasar a "En Curso"), pero no puede solicitarse nuevamente
+ **Estado En Curso:** Solo puede finalizarse o cancelarse por emergencia
+ **Estado Finalizado:** Es un estado terminal, solo permite consulta del historial
+ **Estado Cancelado:** Es un estado terminal, pero puede reprogramarse

Lo anterior conlleva que cada estado tendría validaciones específicas:

- *Solo turnos confirmados pueden generar recordatorios*
- *Solo turnos en curso pueden registrar observaciones médicas*
- *Solo turnos finalizados pueden facturarse*
- *Los turnos cancelados pueden analizarse para estadísticas*
