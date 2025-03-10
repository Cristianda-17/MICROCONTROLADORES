---


---

<h1 id="div-aligncenterinterrupcionesdiv"><div align="center">Interrupciones</div></h1>
<p>Cristian David Sotelo Nieto (134770)<br>
Juan Contreras (134126)<br>
Universidad Ecci<br>
Microcontroladores<br>
Jorge Eduardo Cote<br>
09/03/2025</p>
<hr>
<h2 id="interrupciones-en-un-microcontrolador">Interrupciones en un microcontrolador</h2>
<p>-Las interrupciones son eventos que hacen que el microcontrolador PIC deje de realizar la tarea actual y pase a efectuar otra actividad.<br>
-La mayoría de microcontroladores ofrece una solución para atender algunos tipos de eventos sin ocupar instrucciones en el programa principal<br>
-Se presenta una interrupción cuando el programa principal suspende su ejecución debido a ciertos eventos que detecta el microcontrolador, por ejemplo cambios de estado en puertos de entrada digitales o la finalización de la conversión análoga digital<br>
-Tan pronto como ocurre la interrupción el microcontrolador invoca una rutina de servicio de interrupción (interrupt service routine ISR)</p>
<h3 id="bits-ie-e-if">BITS IE E IF</h3>
<p>IE: (Interrupt enable) habilita el microcontrolador para que detecte ciertos tipos de eventos (llama el ISR)<br>
• Dependiendo de la familia de microcontroladores cada tipo de evento podría tener un IE independiente</p>
<p>IF: (Interrupt flag) indica el estado de la interrupción. Si ocurre la interrupción el microcontrolador la configura en “1”<br>
• Dependiendo de la familia de microcontroladores este bit se configura en cero automaticamente o por instrucción del programador</p>
<h3 id="control-de-interrupcion">Control de interrupcion</h3>
<p>En algunas familias de micorocontroldores se puede encontrar que se comparta un bit de IE para gestionar las interrupciones de varias fuentes, por ejemplo:<br>
En el Motorola HCS12 se comparte el bit IE para activar las interrupciones de los pines de los puertos I/O digitales. Pero cada pin tiene su IF para para detector cual pin detecto el evento</p>
<h3 id="prioridad-de-interrupciones">Prioridad de interrupciones</h3>
<p>Debido a la cantidad de interrupciones, los microcontroladores permiten asignar prioridad a las diferentes llamadas al ISR, dependiendo de la familia de microcontroladores esta prioridad la asigna el programador (PIC) o a través de la table de vectores de interrupción (ATmega16).<br>
La prioridad permite por ejemplo establecer, si una interrupción puede nterrumpir otra interrupción</p>
<h3 id="consideraciones-de-implementación">Consideraciones de implementación</h3>
<ul>
<li>
<p>Se recomienda usar verificación de puertos cuando:<br>
• El operador es un humano<br>
• No require sincronizarse con ningún evento o dispositivo<br>
• El estado es importante<br>
• Los pulsos son de largo periodo de tiempo<br>
• Las señales son ruidosas<br>
• No hay muchas tareas para ejecutar en el main</p>
</li>
<li>
<p>Se recomienda usan interrumciones cuando:<br>
• Los eventos no ocurren periódicamente<br>
• Hay intervalos largos de tiempo entre eventos<br>
• El cambio de estado es importante<br>
• Hay pulsos de corto periodo<br>
• Eventos son generados por hardware<br>
• Se realizan varias tareas en el main</p>
</li>
</ul>
<h3 id="interrupciones-pic-18f4550">Interrupciones PIC 18F4550</h3>
<ol>
<li>
<p>Fuentes de interrupción externa:<br>
• INTx Interrupciones de Pin: Generan interrupción al<br>
detector flancos<br>
• PORTB Interrupción: Un cambio en las entradas<br>
correspondientes provocan una interrupción</p>
</li>
<li>
<p>Fuentes de Interrupciónes internas:<br>
• En la familia de microcontroladores PIC se denominan interrupciones de periférico<br>
• Módulo ADC<br>
• Módulo Timer<br>
• Módulo Comparación<br>
• Módulo PWM<br>
• Modulo Comunicación Serial</p>
</li>
</ol>
<h3 id="orden-de-prioridad">Orden de prioridad</h3>
<p>• Los pic 18F2455/2550/4455/4550 permiten asignar prioridad alta o baja a las interrupciones<br>
• Interrupciones de prioridad alta ubica vectores de interrupción desde 000008h<br>
• Interrupciones de prioridad baja ubica vectores de interrupción desde 000018h<br>
• Para PIC de gama media asignará a todas las interrupciones desde la dirección 000008h (modo de compatibilidad)</p>
<h3 id="interrupciones-por-pin">Interrupciones por pin</h3>
<p>• Son interrupciones producidas por cambio de estado en los pines:</p>
<ul>
<li>RB0/AN12/INT0/FLT0/SDI/SDA</li>
<li>RB1/AN10/INT1/SCK/SCL</li>
<li>RB2/AN8/INT2/VMO</li>
</ul>
<p>• El bit INTEDGX=1 detecta flancos de subida<br>
• El bit INTEDGX=0 detecta flancos de bajada<br>
• Si se detecta un flanco válido la bandera INTxIF=1 y debe apagarse (INTxIF=0) por parte del programador<br>
• Si se hace INTxIE=0 la interrupción se desactivará</p>

