# Poliformismo

El polimorfismo es el principio que permite que objetos de diferentes clases respondan de manera distinta a la misma interfaz o mensaje, manteniendo la capacidad de ser tratados de manera uniforme. Este principio establece que una misma operación puede comportarse de forma diferente según el tipo específico del objeto que la ejecute, permitiendo que el código cliente trabaje con abstracciones sin conocer los detalles específicos de cada implementación concreta, obteniendo reutilización de código genérico flexibilidad y extensibilidad. 

## Relación con principios SOLID

*Si bien la aplicación del los principios SOLID en forma concurrente genera un diseño de sistema eficiente y un estado cumplimiento general de los principios de POO, la relación principal del Poliformismo se da con los siguientes:*

+ **Open/Closed Principle (OCP):** Facilita la extensión del sistema mediante nuevas implementaciones polimórficas sin modificar el código cliente existente, ya que las nuevas clases pueden implementar las mismas interfaces y ser utilizadas de manera intercambiable.

+ **Liskov Substitution Principle (LSP):** El polimorfismo solo funciona correctamente cuando las subclases pueden sustituir completamente a sus clases base sin alterar el comportamiento esperado del sistema, siendo este principio fundamental para que el polimorfismo sea seguro y predecible.

## Relación con patrones de diseño

+ **Patrones Creacionales:** Por ehjemplo, Abstract Factory utiliza polimorfismo donde diferentes factories concretos implementan la misma interfaz de creación, permitiendo que el código cliente use cualquier factory de manera intercambiable sin conocer cuál está usando específicamente, creando familias de productos compatibles polimórficamente.

+ **Patrones Estructurales:** En cuanto a patrones estructurales, Strategy utiliza polimorfismo como su mecanismo central donde diferentes algoritmos implementan la misma interfaz, permitiendo que el contexto cambie de estrategia dinámicamente y trate a todas las estrategias de manera uniforme sin conocer su implementación específica.
  
+ **Patrones de Comportamiento:** En referencia a patrones de comportamiento, Observer utiliza polimorfismo donde diferentes observadores implementan la misma interfaz de notificación, permitiendo que el sujeto notifique a todos los observadores de manera uniforme sin conocer sus tipos específicos. Command emplea polimorfismo donde diferentes comandos concretos implementan la misma interfaz, permitiendo invocar, deshacer y gestionar comandos de manera uniforme independientemente de la operación específica que encapsulen.

## Ejemplo en el proyecto

En el sistema de turnos médicos, el polimorfismo se manifiesta en la jerarquía de profesionales médicos: las clases MedicoClinico, Radiologo y Fisioterapeuta que heredan de Profesional representan un ejemplo perfecto de polimorfismo donde cada especialidad puede responder de manera específica a operaciones médicas comunes. De esta forma, no solo se permite flexibilidad en el diseño, sino que se facilita la extensibilidad y mantenibilidad del código al proporcionar mecanismos para tratar objetos diversos de manera uniforme mientras respetan sus comportamientos específicos.

[**Link Drawio**](https://drive.google.com/file/d/1y0vTbJRasJFrk-96eqUQ9xebRLURWaHm/view?usp=sharing)

![Ejemplo_Poliformismo](imagenes/EJEMPLO_POLIFORMISMO.jpg)

## Ejemplo de Código

    CLASE MedicoClinico HEREDA DE Profesional
         PRIVADO consultorio: cadena

        CONSTRUCTOR MedicoClinico(nombre, apellido, dni, fechaNacimiento, sexo, domicilio, telefono, email, numeroMatricula, vigenciaMatricula, consultorio)
            SUPER(nombre, apellido, dni, fechaNacimiento, sexo, domicilio, telefono, email, "Medicina General", numeroMatricula, vigenciaMatricula)
            ESTE.consultorio = consultorio
        FIN CONSTRUCTOR

        PÚBLICO realizarConsulta(): vacío
            IMPRIMIR "Realizando consulta médica general en consultorio " + consultorio
        FIN MÉTODO

        PÚBLICO prescribirMedicamento(medicamento: cadena): vacío
            IMPRIMIR "Prescribiendo medicamento: " + medicamento
        FIN MÉTODO

        PÚBLICO emitirDiagnostico(): cadena
            RETORNAR "Diagnóstico médico general emitido"
        FIN MÉTODO

    FIN CLASE

    CLASE Radiologo HEREDA DE Profesional
        PRIVADO equipamiento: Lista<cadena>

        CONSTRUCTOR Radiologo(nombre, apellido, dni, fechaNacimiento, sexo, domicilio, telefono, email, numeroMatricula, vigenciaMatricula)
            SUPER(nombre, apellido, dni, fechaNacimiento, sexo, domicilio, telefono, email, "Radiología", numeroMatricula, vigenciaMatricula)
            ESTE.equipamiento = nuevaLista()
        FIN CONSTRUCTOR

        PÚBLICO interpretarImagen(imagen: cadena): cadena
            RETORNAR "Interpretando imagen radiológica: " + imagen
        FIN MÉTODO

        PÚBLICO solicitarEstudio(tipo: cadena): vacío
            IMPRIMIR "Solicitando estudio radiológico: " + tipo
        FIN MÉTODO

        PÚBLICO emitirInforme(): cadena
            RETORNAR "Informe radiológico emitido"
        FIN MÉTODO

    FIN CLASE

    CLASE Fisioterapeuta HEREDA DE Profesional
        PRIVADO certificaciones: Lista<cadena>

        CONSTRUCTOR Fisioterapeuta(nombre, apellido, dni, fechaNacimiento, sexo, domicilio, telefono, email, numeroMatricula, vigenciaMatricula)
            SUPER(nombre, apellido, dni, fechaNacimiento, sexo, domicilio, telefono, email, "Fisioterapia", numeroMatricula, vigenciaMatricula)
            ESTE.certificaciones = nuevaLista()
        FIN CONSTRUCTOR

        PÚBLICO disenarPlanTerapia(): cadena
            RETORNAR "Plan de terapia física diseñado"
        FIN MÉTODO

        PÚBLICO realizarTerapiaFisica(): vacío
            IMPRIMIR "Realizando sesión de terapia física"
        FIN MÉTODO

        PÚBLICO evaluarProgreso(): cadena
            RETORNAR "Evaluación de progreso del paciente"
        FIN MÉTODO

    FIN CLASE

    // Demostración de POLIMORFISMO
    FUNCIÓN demostrarPolimorfismo()
        profesionales: Lista<Profesional> = nuevaLista()
        
        AGREGAR nuevoMedicoClinico(...) A profesionales
        AGREGAR nuevoRadiologo(...) A profesionales
        AGREGAR nuevoFisioterapeuta(...) A profesionales
        
        PARA CADA profesional EN profesionales HACER
            IMPRIMIR profesional.getNombreCompleto() + " - " + profesional.getEspecialidad()
            
            // Polimorfismo: cada subclase implementa validarMatricula de manera específica
            SI profesional.validarMatricula() ENTONCES
                IMPRIMIR "Matrícula válida"
            SINO
                IMPRIMIR "Matrícula vencida"
            FIN SI
        FIN PARA
    FIN FUNCIÓN
