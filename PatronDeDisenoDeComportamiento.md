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

#### Clases del problema original

+ **Turno:** Contiene toda la lógica con condicionales massivos para cada estado
+ **GestorTurnos:** Debe manejar las transiciones de estado y validaciones
+ **EstadoTurno:** Enumeración simple que no encapsula comportamiento

##### Limitaciones del enfoque original

Sin State, la clase Turno tendría:
+ *Métodos llenos de condicionales switch/if para cada estado*
+ *Lógica de transición difícil de mantener*
+ *Violación del principio de responsabilidad única*
+ *Dificultad para agregar nuevos estados o comportamientos*
+ *Código duplicado entre métodos similares*

#### Nuevas clases incorporadas con State:

+ **EstadoTurno (Interfaz)**
  - **Función:** Define el contrato común para todos los estados de un turno
  - **Métodos:** confirmar(), cancelar(), iniciar(), finalizar(), puedeEnviarRecordatorio(), puedeFacturar()
  - **Responsabilidad:** Establecer protocolo común para todos los estados

+ **Turno (Modificado)**
  - **Nueva función:** Mantiene referencia al estado actual y delega operaciones
  - **Atributos añadidos:** estadoActual: EstadoTurno
  - **Métodos modificados:** confirmar(), cancelar(), iniciar(), finalizar()
  - **Beneficio:** Lógica simplificada sin condicionales complejos

+ **EstadoSolicitado (Implementa EstadoTurno)**
  - **Función:** Maneja comportamiento cuando el turno está recién solicitado
  - **Validaciones:** Verifica disponibilidad del profesional antes de confirmar
  - **Comportamientos específicos:**
      * *confirmar(): Válido, transiciona a EstadoConfirmado*
      * *cancelar(): Válido, transiciona a EstadoCancelado*
      * *iniciar(): Inválido, lanza excepción*
      * *puedeEnviarRecordatorio(): false*

+ **EstadoConfirmado (Implementa EstadoTurno)**
  - **Función:** Maneja comportamiento cuando el turno está confirmado
  - **Validaciones:** Verifica tiempo mínimo de anticipación para cancelación
  - **Comportamientos específicos:**
      * *confirmar(): Inválido, ya está confirmado*
      * *cancelar(): Válido, transiciona a EstadoCancelado con penalidad*
      * *iniciar(): Válido, transiciona a EstadoEnCurso*
      * *puedeEnviarRecordatorio(): true*

+ **EstadoEnCurso (Implementa EstadoTurno)**
  - **Función:** Maneja comportamiento cuando el turno está siendo atendido
  - **Validaciones:** Registra tiempo de inicio y profesional atendiendo
  - **Comportamientos específicos:**
      * *confirmar(): Inválido, ya está en curso*
      * *cancelar(): Válido solo por emergencia médica*
      * *finalizar(): Válido, transiciona a EstadoFinalizado*
      * *registrarObservaciones(): Válido y específico de este estado*





EstadoFinalizado (Implementa EstadoTurno)

Función: Maneja comportamiento cuando el turno ha sido completado
Comportamientos específicos:

Todas las operaciones de cambio de estado son inválidas
puedeFacturar(): true
generarResumenAtencion(): Válido y específico de este estado


Validaciones: Registra tiempo de finalización y resultados


EstadoCancelado (Implementa EstadoTurno)

Función: Maneja comportamiento cuando el turno ha sido cancelado
Comportamientos específicos:

Todas las operaciones de cambio son inválidas excepto reprogramar
reprogramar(): Válido, crea nuevo turno en EstadoSolicitado
analizarMotivoCancelacion(): Específico para estadísticas


Validaciones: Registra motivo de cancelación y usuario responsable


HistorialEstados

Función: Registra todas las transiciones de estado del turno
Atributos: estadoAnterior, estadoNuevo, fechaTransicion, usuarioResponsable, observaciones
Responsabilidad: Auditoría completa de cambios de estado


ValidadorTransiciones

Función: Valida que las transiciones de estado sean válidas según reglas de negocio
Método clave: validarTransicion(estadoActual, estadoDestino, contexto)
Responsabilidad: Implementar reglas complejas de transición (horarios, permisos, etc.)
