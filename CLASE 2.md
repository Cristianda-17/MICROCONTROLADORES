---


---

<h1 id="div-aligncenterseñales-digitales-y-análogasdiv"><div align="center">Señales Digitales y Análogas</div></h1>
<p><em>Cristian David Sotelo Nieto (134770)</em><br>
<em>Juan Contreras (134126)</em><br>
<em>Universidad Ecci</em><br>
<em>Microcontroladores</em><br>
<em>Jorge Eduardo Cote</em><br>
<em>09/03/2025</em></p>
<hr>
<h2 id="señales-digitales-y-análogas">Señales Digitales y Análogas</h2>
<p>Las señales analógicas se componen de un rango continuo de valores, donde cada punto puede tener un valor ligeramente diferente. Las señales digitales se componen de una serie de dígitos que son 0 o 1.</p>
<h3 id="puertos-de-entrada-y-salida">Puertos de entrada y salida</h3>
<ul>
<li><em>Interfaz de comunicación</em>: Medio por el cual el microcontrolador recibe y envía información.</li>
<li><em>Bidireccionalidad</em>: Permite tanto la entrada como la salida de datos.</li>
<li><em>Monitoreo y control</em>: Facilita la gestión de hardware externo.</li>
<li><em>Puertos físicos</em>: Conducen señales eléctricas para la transmisión de datos.</li>
<li><em>Tipos de puertos</em>: Pueden ser digitales o análogos, según el tipo de señal manejada.</li>
</ul>
<h3 id="puertos-digitales">Puertos digitales</h3>
<p>Los puertos digitales en un microcontrolador suelen agruparse en bloques de 8 pines, aunque no es una regla fija. Pueden configurarse como entradas, salidas o ser bidireccionales. Los microcontroladores comerciales poseen entre 8 y 32 pines de I/O digitales, aunque algunos, como el Motorola HCS12, pueden superar los 90 pines. Un microcontrolador generalmente cuenta con varios puertos, cuyos pines también pueden ser utilizados por otros módulos internos. La mayoría operan con lógica directa, salvo que el fabricante indique lo contrario.</p>
<h3 id="componentes-típicos">Componentes típicos</h3>
<ul>
<li><em>Data Direction Register (DDR)</em>: Registro que almacena la configuración del puerto, definiendo si se usará como entrada o salida.</li>
<li><em>Port Register (PORT)</em>: Registro que almacena el equivalente lógico de los niveles de tensión en los pines de conexión eléctrica.</li>
<li><em>Port Input Register (PIN)</em>: Generalmente es solo de lectura y contiene el estado actual de todos los pines.</li>
</ul>
<h3 id="entradas-digitales">Entradas digitales</h3>
<p>Los puertos digitales interpretan niveles de tensión del hardware externo, donde un “1” lógico representa un nivel alto (high) y un “0” lógico un nivel bajo (low). Los rangos de tensión varían según el microcontrolador.</p>
<h3 id="configuración-io">Configuración I/O</h3>
<ul>
<li>Lo primero es configurar el registro TRIS para definir si el pin será de entrada o salida. En el PIC 18F4550, el datasheet indica:
<ul>
<li>Si el registro TRIS es “1”, está configurado como entrada.</li>
<li>Si el registro TRIS es “0”, está configurado como salida.</li>
</ul>
</li>
<li>Cargar o leer los datos por medio de los registros LAT o PORT.</li>
</ul>
<h3 id="salidas-digitales">Salidas digitales</h3>
<p>Las salidas digitales de un microcontrolador manejan niveles de tensión y corriente según su familia. Por ejemplo, en el ATmega16, el estado low tiene un máximo de 0.7 V, mientras que el estado high tiene un mínimo de 4.2 V, y la corriente de salida suele estar en el rango de 4-20 mA. Dado que los microcontroladores no cuentan con protecciones internas en los pines de salida, es fundamental implementar estrategias de protección para evitar cortocircuitos. Configurar correctamente el registro DDR como salida conecta el pin al registro PORT, y conocer los valores por defecto de los pines ayuda a tomar acciones en caso de reinicio.</p>

