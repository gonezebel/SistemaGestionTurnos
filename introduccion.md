# Anexo 1 - Introducción al Diseño Orientado a Objetos

## Concepto del Paradigma Orientado a Objetos

La programación orientada a objetos (en adelante POO) es un enfoque conceptual específico para diseñar programas. Este paradigma se concentra en entidades del mundo real como las percibe el usuario, partiendo de la abstracción como objetos, que tienen datos y comportamientos aosciados. 

Lo distintivo de la POO es la técnica de poner todos los atributos y métodos de un objeto en una estructura independiente, la propia clase. En otras palabras, esos objetos son son las "cosas" relevantes para el sistema bajo análisis, mientras que las clases son agrupaciones de objetos que son óptimas para reutilizarse y darles mantenimiento. Una clase define el conjunto de atributos y comportamientos compartidos por cada objeto de la clase. Los programadores deben definir las diversas clases en el programa que escriben, y cuando el programa se ejecuta, los objetos se pueden crear a partir de la clase establecida.

### Diferencias entre la POO y el paradigma de programación estructural

El paradigma estructurado se basa en la división del programa en procedimientos y funciones independientes, con tareas específicas, mientras que la POO se organiza en torno a objetos que son instancias de clases que encapsulan datos y comportamientos relacionados. De esta forma, al crear objetos que contienen datos y código de programación, un cambio en un objeto tiene un impacto mínimo en otros objetos, lo que mejora el mantenimiento, asi como permite la reusabilidad de objetos, reduciendo los costos de desarrollo en sistemas computacionales y facilitando su escalabilidad.


## Los cuatro fundamentos de POO

+ **I. Encapsulación:** Ocultamiento de de detalles internos del objeto, exponiendo solo sus interfaces públicas, favoreciendo, así, la modularidad y la seguridad del sistema.
  
  - *EJ: El control remoto es un objeto que encapsula toda su complejidad interna (circuitos, baterías, sensores infrarrojos) detrás de una interfaz simple (los botones).*
    

    ![Ejemplo encapsulación](imagenes/00_diagrama_encapsulamiento.jpg)


+ **II. Abstracción:**  Simplificar la complejidad de los objetos reales modelando solo los aspectos esenciales relevantes para el sistema.

  - *EJ: El la utilización de un cajero automático por parte de un usuario. La máquina presenta solo funciones simples al usuario (retirar dinero, consultar saldo, transferir) mientras oculta toda la complejidad subyacente. El usuario no necesita entender los sistemas de autenticación, las consultas a bases de datos, los protocolos de comunicación interbancaria o los mecanismos de seguridad que operan tras cada botón que presiona.*
    

    ![Ejemplo abstracción](imagenes/01_diagrama_abstracción.jpg)


+ **III. Herencia:** Permite que un objeto obtenga propiedades y comportamientos de otro objeto, a través de una jerarquía de clases, permitiendo la reutilización del código.

  - *EJ: Los vehículos de transporte automotor representan un ejemplo herencia. Todos los vehículos comparten características comunes (motocicletas, automóviles, camiones, etc), pero cada tipo específico tiene sus propias peculiaridades.*
    

    ![Ejemplo herencia](imagenes/02_diagrama_herencia.jpg)


+ **IV. Polimorfismo:**:  Capacidad de los objetos de una misma jerarquía de clases para responder de manera diferente a un mismo mensaje, permitiendo flexibilidad a través de código genérico.

   - *EJ: Los instrumentos musicales de una orquesta, donde cada instrumento (violín, trompeta, piano) hereda de la clase base InstrumentoMusical e implementa el método tocar_nota() según su naturaleza física única. Cuando el director solicita "tocar Do", está invocando el mismo método en objetos de diferentes clases, pero cada uno produce el sonido de manera distinta: el violín mediante cuerdas vibradas con un arco, la trompeta a través de vibraciones de aire en un tubo metálico, y el piano golpeando cuerdas con martillos*
     

    ![Ejemplo poliformismo](imagenes/03_diagrama_poliformismo.jpg)


## Requisitos iniciales del sistema

+ **I. Protección de datos personales:** Solo el personal autorizado podrá acceder a los datos sensibles de contacto tanto de pacientes como de médicos, garantizando la privacidad.

+ **II. Alta de pacientes y profesionales:**  El sistema brindará la posibilidad de incorporar nuevos registros de pacientes y médicos al sistema de forma sencilla y organizada.

+ **III. Distribución de turnos según disponibilidad:** La asignación de turnos se realizará teniendo en cuenta los horarios disponibles de cada profesional de la salud.

+ **IV. Visualización de agenda médica:** Cada médico podrá acceder a un calendario donde visualizará todos los turnos que tiene programados.

+ **V. Avisos automáticos:** El sistema enviará comunicaciones por correo electrónico y/o mensajes de Whatsapp a pacientes para informar sobre confirmaciones, cancelaciones o cambios en los turnos.


## Casos de uso

+ **I. Registrar un paciente nuevo al sistema**

  - *Actor(es):* Personal de atención al paciente
  - *Descripción:* El personal carga la información de un paciente que aún no figura en la base.
  - *Flujo principal:*
      * a. El personal inicia sesión en el sistema con credenciales con permisos suficientes para la acción.
      * b. Navega al módulo de gestión de pacientes.
      * c. Selecciona la opción "Registrar nuevo paciente".
      * d. El sistema muestra un formulario con los campos requeridos.
      * e. Se completan los campos con apellido y nombre, tipo y número de documento o identificación, fecha de nacimiento,             sexo, domicilio, datos fiscales, tipo e identificación de cobertura de salud y datos de contacto.
      * f. El sistema verifica automáticamente que el paciente no exista previamente utilizando tipo y numero de documento.
      * g. Si la verificación es exitosa, el personal hace clic en "Guardar".
      * h. Se guarda la información y se muestra un mensaje confirmando la operación.
      * i. El sistema ofrece opción para registrar otro paciente.
  - *Precondición:* El paciente no debe estar previamente registrado.
  - *Postcondición:* El paciente se agrega correctamente a la base de datos.


+ **II. Registrar un nuevo profesional de la salud**

  - *Actor(es):* Personal administrativo, de recursos humanos o del sector con potestad para la tarea
  - *Descripción:* El personal autorizado ingresa los datos de un médico que comenzará a atender en el centro.
  - *Flujo principal:*
      * a. El personal inicia sesión en el sistema con credenciales con permisos suficientes para la acción.
      * b. Accede al módulo administrativo del sistema.
      * c. Selecciona la opción "Gestión de profesionales".
      * d. Elige "Registrar nuevo profesional".
      * e. El sistema muestra un formulario con los campos requeridos.
      * f. Se completan los campos obligatorios: nombre completo, tipo y numero de documento, fecha de nacimiento, sexo,     
           domicilio, datos fiscales, especialidad, tipo y número de matrícula profesional, vigencia de matrícula y datos de            contacto.
      * g. El sistema verifica que el profesional no exista previamente por tipo y numero de matricula y DNI.
      * h. Si la verificación es exitosa, el personal hace clic en "Guardar".
      * i. Se guarda la información y se muestra un mensaje confirmando la operación.
      * j. El sistema permite cargar información administrativa relacioanda a pago de honorarios o ingresar otro médico.
  - *Precondiciones:* El médico no debe estar previamente cargado en el sistema.
  - *Postcondiciones:* El profesional queda disponible para la asignación de turnos y visible en la agenda médica.


+ **III. Asignar un turno con un médico para un paciente**

  - *Actor(es):* Paciente, personal de atención al paciente
  - *Descripción:* Se agenda una consulta para un paciente, respetando la disponibilidad del profesional.
  - *Flujo principal:*
      * a. El personal o paciente inicia sesión en el sistema.
      * b. Accede al módulo de "Gestión de turnos".
      * c. Selecciona "Agendar nuevo turno".
      * d. El sistema solicita identificar al paciente por DNI.
      * e. Una vez identificado el paciente, el sistema muestra sus datos básicos y cobertura.
      * f. El usuario selecciona el profesional mediante busqueda por nombre, especialidad y horarios disponibles.
      * g. El sistema muestra la disponibilidad del profesional.
      * h. El usuario selecciona fecha y hora disponibles.
      * i. El sistema verifica requisitos adicionales para el turno (Autorizaciones, prescripciones, estudios previos)
      * j. En caso de requerir autorización solicita token.
      * k. El sistema y el validador de la cobertura aprueban o no el token.
      * l. En caso afirmativo, se permite registrar información adicional como sintomas, motivos, aclaraciones.
      * m. El usuario confirma el turno.
      * n. Se registra el turno en la base con código único de turno, se bloquea la agenda y se genera comprobante de turno.
  - *Precondición:* El profesional debe tener disponibilidad en el horario elegido y el paciente debe cumplimentar posibles                      prescripciones médicas aplicables así como también validacion de cobertura (incluyendo verificación de                       token de autorización).
  - *Postcondición:* El turno queda registrado y se envía un aviso correspondiente.


+ **IV. Anular un turno programado**
 
  - *Actor(es):* Paciente, personal de atención al paciente
  - *Descripción:* El turno puede ser cancelado por el paciente o por el personal del centro de salud ante un imprevisto.
  - *Flujo principal:*
      * a. El paciente o personal inicia sesión en el sistema.
      * b. Accede al módulo "Gestión de turnos".
      * c. Selecciona "Consultar/Modificar turnos".
      * d. El sistema solicita identificación:
                Para paciente: documento o código de paciente
                Para personal: datos del paciente o código de turno
      * e. El sistema muestra la lista de turnos vigentes.
      * f. El usuario selecciona el turno a cancelar.
      * g. El sistema muestra los detalles completos del turno.
      * h. El usuario selecciona "Anular turno".
      * i. El sistema solicita el motivo de cancelación con opciones.
      * j. El usuario completa el motivo de cancelación.
      * k. El sistema verifica la política de cancelación en cuanto a tiempos de anticipacion y posibles penalidades.
      * l. El usuario confirma la anulación.
      * m. El sistema Actualiza el estado del turno a "Cancelado", libera la agenda del médico, registra la fecha y hora de             anulación y el motivo.
      * n. El sistema envía notificaciones al médico, al paciente y al área administrativa.
      * ñ. El sistema ofrece la opción de reprogramar o finalizar la gestión.

  - *Precondición:* El turno debe estar vigente.
  - *Postcondición:* El turno se anula y se libera el espacio correspondiente en la agenda.


+ **V. Envío de recordatorios de turnos**

  - *Actor(es):* Gestor de turnos (módulo de automatización de funciones), servidor de mail o mensajería instantánea.
  - *Descripción:* El sistema se encarga de recordar al paciente que tiene una cita próxima.
  - *Flujo principal:*
      * a. El módulo de gestión de recordatorios se activa automáticamente según programación.
      * b. El sistema consulta la base de datos de turnos programados.
      * c. Identifica los turnos próximos según reglas predefinidas.
      * d. Para cada turno identificado recupera los datos y referencia de contacto del paciente.
      * e. El sistema genera el contenido personalizado del recordatorio.
      * f. Envía un mensaje por correo electrónico o mensaje de Whatsapp.
      * g. El paciente recibe la notificación
      * h. El paciente confirma asistencia o solicita cancelación.
  - *Precondición:* Debe haber un turno programado.
  - *Postcondición:* El paciente recibe el aviso a tiempo.
 
+ **VI. Crear Agenda para un Médico**

  - *Actor(es):* Personal administrativo, Coordinador médico, Profesional de la salud
  - *Descripción:* Se configura la disponibilidad del profesional médico en el sistema, estableciendo días, horarios,     
     duración de turnos y consultorio asignado para la atención de pacientes.
  - *Flujo principal:*
      * a. El personal autorizado inicia sesión en el sistema con credenciales válidas.
      * b. Navega al módulo de "Gestión de agenda médica".
      * c. Selecciona la opción "Crear/Configurar agenda".
      * d. El sistema solicita identificar al profesional mediante DNI, nombre y apellido o número de matrícula.
      * e. Una vez identificado el profesional, el sistema muestra sus datos básicos.
      * f. El usuario selecciona el período de configuración de agenda: Fecha de inicio, fecha de finalización (opcional),              frecuencia de repetición, con restricciones de los horarios comerciales del centro de salud y los horarios de                contrato del profesional de la salud.
      * g. El usuario asigna el consultorio para cada día de atención mediante la disponibilidad existente y las             
           restricciones físicas o comerciales que disponga el centro de salud.
      * h. En base al estandar de tiempos de atención por especialidad configurado previamente, el sistema calcula la                   cantidad de turnos disponibles en el rango horario configurado cada dia.
      * i. El sistema solicita configuración de excepciones como vacaciones, feriados, licencias, entre otras.
      * j. El usuario establece reglas específicas de agenda como cantidad permitida de sobreturnos, restricciones de                   atención por cada tipo de cobertura de salud, entre otras.
      * k. El usuario confirma la creación de la agenda.
      * l. El sistema muestra un resumen de la agenda creada con datos principales.
      * m. El sistema ofrece opciones para imprimir resumen de agenda, enviar detalle al profesional por correo, registrar              otra agenda o volver al menú principal.
  - *Precondición:*
        i.  El profesional debe estar correctamente registrado en el sistema.
        ii. El usuario debe tener permisos para gestionar agendas médicas.
        iii.Los consultorios deben estar previamente configurados en el sistema.
  - *Postcondición:*
        i.  El paciente recibe el aviso a tiempo.
        ii. Los horarios definidos quedan disponibles para asignación de turnos.
        iii.El consultorio queda reservado para el profesional en los días y horarios establecidos.
        iv. El sistema habilita la visualización de la disponibilidad para el personal de turnos.
      

## Boceto inicial del diseño de clases

[**Link Drawio**](https://drive.google.com/file/d/1vFd70BRh0BuMLam6-RxGJqXAKmhSRiL2/view?usp=sharing)

![Boceto diseño de clases](imagenes/04_clases_sistema_POO.jpg)


 
