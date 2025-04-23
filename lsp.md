# Principio de Sustitución de Liskov (LSP) 

El principio LSP establece que una subclase debe poder sustituir a su superclase sin alterar el comportamiento esperado del sistema. Es decir, los objetos derivados deben poder ser utilizados donde se espera un objeto de la clase base, sin provocar efectos inesperados o romper la lógica del programa. Esto promueve la coherencia jerárquica, el uso seguro de la herencia y mejora la extensibilidad del código.

Es posible aplicar este principio a la jerarquía entre las clases Persona, Paciente y Profesional, garantizando que ambos puedan usarse indistintamente como Persona sin afectar la lógica general del sistema. El mal uso de la herencia puede romper este principio si alguna subclase no cumple con los contratos esperados por su clase base.

# Motivación 
 
En el diseño original, Persona define atributos comunes como nombre, apellido, DNI y contacto, y se espera que sus subclases respeten ese contrato básico. Sin embargo, si Paciente o Profesional sobrescriben comportamientos o agregan restricciones que contradicen o ignoran las expectativas definidas en Persona, se rompe el principio de sustitución.

Por ejemplo:

  I. Si Persona tiene un método getContacto() que debe retornar un medio válido de comunicación, pero Paciente lo sobrescribe devolviendo null porque la comunicación es solo vía app, se rompe la expectativa.

  II.  Si Profesional redefine el comportamiento de getNombreCompleto() para incluir su matrícula médica, podría alterar lógicas que solo esperan datos civiles.

Esto equivale a tener un formulario que espera un "ciudadano" con nombre y DNI, y al colocar allí un "médico", este exige matrícula y especialidad para mostrar su nombre, invalidando el uso del formulario.

# Estructura de Clases 
 

