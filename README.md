# Investigación Memoria de Titulación 2020

## Tema de memoria en el área de ciberseguridad

La investigación que llevo hasta la fecha (fecha inicio marzo 2020) la he realizado en los siguientes temas.

1. Lectura de papers en los tópicos de inteligencia artificial y ciberseguridad (resúmenes en el git).
2. Listado de metodologías y herramientas para realizar penetration testing.
3. Resumen de tutoriales (comandos) de las herramientas encontradas (pentesting).
4. Metodologías y resumen de tutoriales para hacer Fuzzing (fuzzing en general y también enfocado en Web Apps).

## Definición del tema de memoria
Ahora hay que acotar y converger a un problema específico.

El problema que hemos logrado identificar es que los aportes al código por parte de los developers no son centralizados. Si bien los aportes se revisan entre parejas, no existe un "revisor universal" para verificar que no se estén incorporando vulnerabilidades al código.

El desconocer qué nuevas vulnerabilidades se introducen con el cambio del código, no se pueden tomar decisiones con respecto a la seguridad de la app.

El approach para abordar la problemática, en primera instancia, es hacer un sistema que se comunique con los pull requests (PR) y sea capaz de identificar vulnerabilidades en el código (puede ser código estático o código en "vivo") para luego generar un reporte (algún warning) sobre el estado del código. Si logra encontrar vulnerabilidades, entonces este rechaza el PR para ser corregido.
