# Anexo - Aplicación de patrón de diseño estructural - Adapter

Los patrones de diseño estructurales explican cómo ensamblar objetos y clases en estructuras más grandes, a la vez que se mantiene la flexibilidad y eficiencia de estas estructuras. Estos patrones se ocupan de la composición de clases y objetos para formar estructuras más complejas y resolver problemas de incompatibilidad entre interfaces.

### Relación con principios SOLID:

+ **SRP (Single Responsibility Principle):** Separan la responsabilidad de adaptación de la lógica de negocio principal
+ **OCP (Open/Closed Principle):** Permiten integrar nuevos sistemas sin modificar código existente
+ **DIP (Dependency Inversion Principle):** Facilitan que el código dependa de abstracciones en lugar de implementaciones específicas
+ **ISP (Interface Segregation Principle):** Evitan que las clases dependan de interfaces que no utilizan

### Propósito y tipo del patrón

Adapter es un patrón de diseño estructural que permite que objetos con interfaces incompatibles colaboren entre sí; actúa capturando llamadas de un objeto y transformándolas al formato e interfaz reconocible por el segundo objeto.

### Problema resuelto

El sistema necesita validar coberturas médicas y obtener autorizaciones de múltiples obras sociales y prepagas, cada una con su propio sistema, protocolo de comunicación y formato de datos. Estas entidades externas tienen APIs incompatibles entre sí.

### Solución

El patrón Adapter crea adaptadores específicos para cada obra social que traducen las llamadas del sistema interno al formato requerido por cada entidad externa, permitiendo una integración transparente.

## Motivación

### Problema detallado

El sistema debe verificar autorizaciones de cobertura médica y generar tokens para validar que los pacientes tienen derecho a la atención. En el mercado local existen múltiples obras sociales y prepagas, cada una con sistemas tecnológicos diferentes, por lo cual el desafío técnico radica en que el sistema interno necesita una interfaz uniforme para validar coberturas, pero cada obra social tiene:

  - **Protocolos de comunicación diferentes** (REST, SOAP, FTP)
  - **Formatos de datos incompatibles** (JSON, XML, texto plano)
  - **Métodos de autenticación distintos** (OAuth2, certificados, tokens custom)
  - **Campos de datos con nombres y estructuras diferentes**

#### Clases del problema original

+ **ValidadorCobertura:** Necesita validar autorizaciones pero no puede manejar múltiples interfaces incompatibles
+ **Paciente:** Contiene información de cobertura pero en formato estándar interno
+ **Turno:** Requiere validación de autorización antes de confirmar

##### Limitaciones del enfoque original

Sin Adapter, el ValidadorCobertura tendría que:

+ **Conocer los protocolos específicos de cada obra social**
+ **Manejar múltiples formatos de datos incompatibles**
+ **Implementar diferentes métodos de autenticación**
+ **Ser modificado cada vez que se agrega una nueva obra social**
+ **Violar el principio de responsabilidad única al mezclar lógica de validación con integración**

#### Nuevas clases incorporadas con Adapter:

+ **InterfazCoberturaMedica (Interfaz)**
  - **Función:** Define el contrato común para todas las validaciones de cobertura
  - **Métodos:** validarCobertura(), obtenerAutorizacion(), verificarVigencia()
  - **Responsabilidad:** Establecer protocolo estándar interno

+ **DatosCoberturaEstandar**
  - **Función:** Formato de datos unificado para el sistema interno
  - **Atributos:** numeroAfiliado, planCobertura, vigenciaDesde, vigenciaHasta
  - **Responsabilidad:** Encapsular información de cobertura en formato estándar

+ **AdaptadorOSDE (Implementa InterfazCoberturaMedica)**
  - **Función:** Adapta las llamadas internas al API REST de OSDE
  - **Responsabilidades:**
      * *Transformar DatosCoberturaEstandar a formato JSON de OSDE*
      * *Manejar autenticación OAuth2 con OSDE*
      * *Convertir respuestas JSON a objetos internos*
      * *Gestionar errores específicos del API de OSDE*
  
+ **AdaptadorSwissMedical (Implementa InterfazCoberturaMedica)**
  - **Función:** Adapta las llamadas internas al servicio SOAP de Swiss Medical
  - **Responsabilidades:**
      * *Crear mensajes SOAP XML desde datos internos*
      * *Manejar certificados SSL y autenticación*
      * *Parsear respuestas XML a objetos internos*
      * *Gestionar timeout y reconexión del servicio SOAP*

+ **AdaptadorIOMA (Implementa InterfazCoberturaMedica)**
  - **Función:** Adapta las llamadas internas al sistema FTP de IOMA
  - **Responsabilidades:**
      * *Generar archivos de consulta en formato texto plano*
      * *Manejar conexión FTP segura*
      * *Procesar archivos de respuesta con formato fijo*
      * *Gestionar colas de procesamiento batch*

+ **AdaptadorOSECAC (Implementa InterfazCoberturaMedica)**
  - **Función:** Adapta las llamadas internas al API de la Obra Social de Empleados de Comercio
  - **Responsabilidades:**
      * *Transformar datos a formato propietario JSON*
      * *Manejar tokens de autenticación custom*
      * *Convertir códigos de error específicos*
      * *Gestionar límites de rate limiting del API*
        
+ **ValidadorCobertura (Modificado)**
  - **Nueva función:** Utiliza adaptadores sin conocer implementaciones específicas
  - **Método principal:** validarAutorizacion(paciente: Paciente, tipoConsulta: String)
  - **Beneficio:** Lógica de validación desacoplada de integraciones externas

+ **FactoryAdaptadores**
  - **Función:** Crear el adaptador correcto según la obra social del paciente
  - **Responsabilidad:** Encapsular la lógica de selección de adaptador
  - **Método clave:** crearAdaptador(codigoObraSocial: String): InterfazCoberturaMedica

#### Ventajas de la nueva estructura:

+ **Compatibilidad:** Integración transparente con múltiples sistemas incompatibles
+ **Extensibilidad:** Fácil agregar nuevas obras sociales creando nuevos adaptadores
+ **Mantenibilidad:** Cambios en APIs externas solo afectan su adaptador específico
+ **Reutilización:** Los adaptadores pueden usarse en otros módulos del sistema
+ **Cumplimiento SOLID:**
    - *SRP:* Cada adaptador tiene una responsabilidad específica
    - *OCP:* Abierto para nuevas obras sociales, cerrado para modificación
    - *DIP:* ValidadorCobertura depende de la abstracción, no de implementaciones

## Estructura de clases


