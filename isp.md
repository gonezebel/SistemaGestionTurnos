# Principio de Segregación de Interfaces (ISP) 
El ISP pregona que contar con más interfaces cliente específicas es mas eficiente que contar con una única interfaz general, de modo tal que los clientes no sean forzados a utilizar intefaces que no usan por completo, y por ende también a estar sujetos a los cambios en ellas. La aplicación de este principio promueve la cohesión, reduce el acoplamiento y facilita el mantenimiento del código al minimizar el impacto de los cambios.

Es posible aplicar este principio a la jerarquía de clases relacionadas con los profesionales médicos en el sistema de turnos, segregando las responsabilidades según las especialidades y capacidades específicas de cada tipo de profesional.
 
# Motivación 

En el diseño original, podríamos tener una única interfaz ServicioMedico con todos los métodos posibles que cualquier profesional de la salud podría realizar. Sin embargo, esto obligaría a cada especialista a implementar métodos irrelevantes para su función. Para respetar el ISP, debemos dividir esta interfaz general en interfaces más pequeñas y cohesivas que reflejen las capacidades específicas de los diferentes tipos de profesionales.

Por ejemplo:
 + I. Un Medico Clínico necesita realizar consultas y prescribir medicamentos, pero no necesita interpretar imágenes radiológicas.
+ II. Un Técnico/Médico Radiólogo necesita interpretar imágenes diagnósticas, pero no necesita diseñar planes de fisioterapia.
+ III. Un Fisioterapeuta necesita realizar terapias físicas y diseñar planes de rehabilitación, pero no necesita prescribir medicamentos.
  
# Estructura de Clases 
