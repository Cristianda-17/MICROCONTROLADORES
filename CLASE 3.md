---


---

<h1 id="div-aligncenterentradas-y-salidas-analogas-analog-10-div"><div align="center">Entradas y salidas analogas Analog 1/0 </div></h1>
<p>Cristian David Sotelo Nieto (134770)<br>
Juan Contreras (134126)<br>
Universidad Ecci<br>
Microcontroladores<br>
Jorge Eduardo Cote<br>
09/03/2025</p>
<hr>
<h2 id="señales-analogicas">Señales analogicas</h2>
<p>Son aquellas que pueden tomar<br>
cualquier nivel de tensión dentro de un rango<br>
determinado de funcionamiento. La mayoría de las<br>
señales del ambiente son analógicas, por ejemplo la<br>
temperatura, la luz, el sonido, etc.</p>
<h3 id="entradas-digitales-vs-analogicas">Entradas digitales vs analogicas</h3>
<p>-La señas analogica puede  tomar cualquier valor en el dominio</p>
<p>-La Señal digital tiene solo 2 posibles valores o estados. Su forma de<br>
onda es cuadrada</p>
<h3 id="conversion-digital-a-analoga">Conversion digital a analoga</h3>
<p>Algunos microcontroladores poseen salidas analógicas<br>
que permiten representar valores binarios en una señal<br>
eléctrica de voltaje<br>
• Para el caso en que no se tenga salida analógica:<br>
Usar señal de PWM y aplicar un filtro en la salida para<br>
obtener el valor promedio o Usar un circuito resistivo de ponderación binaria</p>
<h3 id="conversion-analog-digital">Conversion analog digital</h3>
<p>Teniendo en cuenta que el microcontrolador es un dispositivo digital las señales analógicas no podrán ser procesadas directamente por el microcontrolador por lo tanto es necesario realizar una conversión de la señal análogica<br>
a una representación digital que pueda ser procesada por el microcontrolador</p>
<h3 id="procedimiento-de-conversion">Procedimiento de conversion</h3>
<ol>
<li>
<p>Muestreo :<br>
Medir valores de voltaje cada cierto tiempo, se mide como el número de veces que se mide en 1 segundo por lo tanto la unidad es Hz, Entre más alta sea la tasa de muestreo más información se está procesando.<br>
Si la tasa es muy baja se pierde mucha información y no se puede reconstruir fielmente la señal, La tasa de muestreo debe ser mínimo del doble de la frecuencia de la señal que se está muestreando</p>
</li>
<li>
<p>Cuantificacion:<br>
La señal análoga se convierte en una serie de valores que corresponden a cada una de las medidas tomadas en el muestreo</p>
</li>
<li>
<p>Codificacion:<br>
Se asignan valores de tipo binario a cada uno de los valores de la cuantización, los valores a usar los define el diseñador de acuerdo al tipo de información obtenida en la cuantización.<br>
Lo más usual es que se utilice código binario para representar cada valor de voltaje</p>
</li>
</ol>
<h3 id="tecnicas-de-conversion-adc">Tecnicas de conversion ADC</h3>
<ul>
<li>Flash converter: Para cada nivel de comparación se require hardware adicional. Son costosos<br>
. Tracking converter:  Almacena en un Contador el estimado digital del actual voltaje de entrada. El valor digital del Contador es convertido a su análogo y comparado con el voltaje de entrada. Si el voltaje de entrada es mayor que el actual valor del Contador el Contador se incrementa, sino se decrementa</li>
<li>Successive approximation converter: En la mayoría de microcontroladores este es el tipo de conversor que se utiliza</li>
</ul>
<h2 id="microcontrolador-pic18f4550">Microcontrolador PIC18F4550</h2>
<p>Características<br>
• Resolución: 10 bits<br>
• 10 entradas (28 pines)<br>
• 13 entradas (40/44 pines)<br>
• Rango de entrada: [0,5], [0,3], [0, -3]<br>
• Tiempo de adquisición variable</p>
<h3 id="procedimiento-de-conversion-1">Procedimiento de conversion</h3>
<ol>
<li>Configurar el modulo A/D<br>
• Configure las entradas en modo analógico y la tensión de<br>
referencia a usar<br>
• Seleccione el canal A/D<br>
• Configure el tiempo de adquisición<br>
• Seleccione el ajuste de reloj de conversión<br>
• Encienda el conversor A/D</li>
<li>Configure la interrupción A/D (opcional)</li>
<li>Espere el tiempo de adquisición (opcional)</li>
<li>Inicie la conversión</li>
<li>Espere la terminación de la conversión para reiniciarla</li>
<li>Lea los resultados desde los registros correspondientes</li>
<li>Repita el procedimiento</li>
</ol>
<p>Como conclusion nos damos cuenta que la conversion A/D es necesaria para procesar señales<br>
procedentes de sensores analógicos y que la mayoria de microcontroladores ya tienen este tipo de modulo integrado</p>

