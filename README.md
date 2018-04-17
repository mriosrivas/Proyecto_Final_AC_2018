# Proyecto Final Arquitectura del Computador 1

## Primera Parte (10 pts.)
Realizar una presentación que resuma todos los conceptos aprendidos en clase. La misma no debe durar más de 10 minutos, pero debe incluir la mayoría de temas vistos en clase. Trate de ser creativo en su presentación. La fecha de presentación será el **Miércoles 25 de Abril en horario de clase**.


## Segunda Parte (20 pts.)
### 1. Implementar el soft-processor Microblaze en la tarjeta Basys 3 utilizando Vivado.

Para implementar este procesador es necesario que investiguen en que consiste el procesador Microblaze. Su arquitectura intera y su principio de funcionamiento. Es importante que investiguen en que consisten los GPIOs y que es un Canal. En clase se dará un laboratorio de implementación de este procesador para que el alumno se familiarice con los conceptos generales del procesador Microblaze.

Algunas referencias de ayuda al estudiante son las siguientes:

* [Getting Started with the Vivado IP Integrator](https://reference.digilentinc.com/vivado/getting-started-with-ipi/start)
* [Basys 3 Getting started in Microblaze](https://reference.digilentinc.com/learn/programmable-logic/tutorials/basys-3-getting-started-with-microblaze/start)
* [Microblaze Cheat Sheet](http://soerenbnoergaard.dk/notes/dd/microblaze-c-reference.pdf)


### 2. Utilizar los siguientes periféricos:
En el desarrollo del proyecto se solicita que los periféricos utilizados sean los siguientes:

a.  Display de 7 segmentos (GPIO 1)
    1. Anodo (Channel 1)
    2. Cátodo (Channel 2)

b. 4 Pulsadores (GPIO 2, Channel 1)

c. 16 Stwitches (GPIO 2, Channel 2)

d. UART


### 3. Descripción del Proyecto
El proyecto consiste en implementar una rutina que permita al usuario almacenar una contraseña por la
computadora en el procesador Microblaze, la misma debe de ser de cuatro letras minúsculas de la a-z. 

Para ingresar la contraseña el usuario debe de introducir letra por letra con los Switches. El orden de ingreso debe de ser de la letra que esté más a la derecha hasta llegar a la más izquierda. Por ejemplo, si la palabra clave fuera *"hola"*, la primera letra a ingresar sería la *"a"*, luego la *"l"*, luego *"o"* y por último la *"h"*.

El diccionario que se muestra abajo presenta la manera de representar cada letra:

dictionary = {"a":0 , "b":2, "c":3, ... , "z":25}

Al ingresar una contraseña correcta el display debe de indicar *"OPEN"*, en caso contrario se debe de mostrar *"Err"*.

### 4. Entrega y Presentación
El proyecto debe de ser subido al repositorio de cada grupo en una carpeta llamada Final. Deben de incluirse todos los archivos, tanto el proyecto de Vivado como el proyecto de SDK.

Debe de realizarse una presentación por grupo de no más de 10 minutos donde incluyan sus resultados, implementación y consideraciones a la hora de realizar su proyecto.

La fecha de presentación será el **Sábado 5 de Mayo a las 8:00 AM**.

