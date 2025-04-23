# Principio de Responsabilidad Única (SRP)

El SRP establece que una clase debe tener una única razón para cambiar, es decir, una sola responsabilidad bien definida. Esta definición implica limitar el impacto de los cambios en el sistema, haciendolos mas fácil de implementar, dado que al darse clases claramente definidas se minimizan los efectos colaterales en otras.

## Motivación

En el diseño original, la clase Paciente tiene múltiples responsabilidades:

  + Almacenar información personal (heredada de Persona)
  + Gestionar sus propios turnos (solicitar, confirmar, cancelar)
  + Consultar su historial de prescripciones
  + Manejar su información de cobertura médica

Esta concentración de responsabilidades puede ocasionar problemas como:

  ++ Si cambia la lógica de gestión de turnos, debemos modificar la clase Paciente
  ++ Si cambia el sistema de coberturas médicas, también debemos modificar Paciente
  ++ Si cambia cómo se accede a las prescripciones, nuevamente debemos modificar la misma clase

## Estructura de Clases 
