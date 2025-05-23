# Principio de Segregación de Interfaces (ISP) 
El ISP pregona que contar con más interfaces cliente específicas es mas eficiente que contar con una única interfaz general, de modo tal que los clientes no sean forzados a utilizar intefaces que no usan por completo, y por ende también a estar sujetos a los cambios en ellas. La aplicación de este principio promueve la cohesión, reduce el acoplamiento y facilita el mantenimiento del código al minimizar el impacto de los cambios.

Es posible aplicar este principio a la jerarquía de clases relacionadas con los profesionales médicos en el sistema de turnos, segregando las responsabilidades según las especialidades y capacidades específicas de cada tipo de profesional.
 
## Motivación 

En el diseño original, podríamos tener una única interfaz ServicioMedico con todos los métodos posibles que cualquier profesional de la salud podría realizar. Sin embargo, ésto obligaría a cada especialista a implementar métodos irrelevantes para su función. Para respetar el ISP, debemos dividir esta interfaz general en interfaces más pequeñas y cohesivas que reflejen las capacidades específicas de los diferentes tipos de profesionales.

Por ejemplo:
+ Un medico clínico necesita realizar consultas y prescribir medicamentos, pero no necesita interpretar imágenes radiológicas.
+ Un técnico/médico radiólogo necesita interpretar imágenes diagnósticas, pero no necesita diseñar planes de fisioterapia.
+ Un fisioterapeuta necesita realizar terapias físicas y diseñar planes de rehabilitación, pero no necesita prescribir medicamentos.
  
## Estructura de Clases 

[Link drawio](https://drive.google.com/file/d/1bpLAHIN75-rAq2f_ZS1Fsg5ckWt631E_/view?usp=sharing)
![Ejemplo ISP](imagenes/021_Parcial_1_SOLID_ISP.jpg)

