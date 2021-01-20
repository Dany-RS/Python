# Python
Servicio Mensajería - Clases, BBDD, Web scrapping, tratamiento ficheros, consola, formateos.

Nuestra empresa nos solicita crear una aplicación que va a gestionar mensajes obtenidos desde diversas redes sociales.

Cada mensaje se caracteriza por el nick del usuario, el nombre de la red social (Facebook, twiter, ect.), la fecha en la que se publicó el mensaje y el texto del mensaje.

Los mensajes son adquiridos de diversas maneras:

- Algunos son proporcionados directamente, sin ningún formato específico.

- Otros son adquiridos a terceros, los cuales nos proporcionan un fichero de texto formado por líneas. Dentro de estos ficheros, cada mensaje comienza con una línea con el nombre de la red social, el Nick y la fecha separados por comas, seguido por las líneas que forman el mensaje y seguido de una línea en blanco que separa el siguiente mensaje.

-  Otros son adquiridos formando parte del código de una página HTML correspondiente a una red social concreta. La estructura de estas páginas HTML es similar a la siguiente (Código comentado para que no de errores al mostrarlo en github):
<!--
<h1>Nombre de la red social</h1>
<div class='mensaje'>
   <p>Nick</p>
   <date>la fecha en formato UTC (año-mes-día)</date>
   <article>El texto del mensaje</article>
</div>
<div class='mensaje'>
   <p>Nick</p>
   <date>la fecha en formato UTC (año-mes-día)</date>
   <article>El texto del mensaje</article>
</div>
-->
Nuestra empresa quiere almacenar todos los mensajes, en un mismo formato, dentro de una base de datos. Esta base de datos constará de varias tablas:

-  Una tabla "red_social". En cada registro se guardará un código numérico único (la clave), el nombre de la red social, y la url de acceso a la red social.

-  Una tabla "usuario". En cada registro se guardará un código entero (la clave), el Nick y código de la red social donde usa el Nick, el nombre completo del usuario, y la dirección de correo electrónico del usuario (si se conoce).

-  Una tabla "mensaje". En cada registro se guardará un código entero (la clave), un código de usuario, la fecha del mensaje, y el texto del mensaje.

Hay que construir una interfaz de usuario que permita añadir a la base de datos mensajes desde cada una de las fuentes. En cada caso se proporcionará directamente los datos del mensaje, la ruta del fichero de texto, o la url de la página web.

Aplica una solución orientada a objetos usando clases. Crea una clase Mensaje que almacene en memoria los datos de un mensaje. Crea una clase ProcesadorMensajes que contenga todas las operaciones necesarias para recibir los datos directos un mensaje y almacenarlo en la base de datos; piensa qué métodos debería proporcionar esta clase. Crea subclases ProcesadorFileMensajes y ProcesadorHtmlMensajes que hagan lo propio para recuperar mensajes desde un fichero de texto y desde una página HTML. En las subclases reescribe los métodos que lo necesiten, pero procura reutilizar, tal cual, el mayor número posible de métodos de la superclase.

Hay que construir una interfaz de usuario que permita consultar la base de datos de mensajes para obtener estadísticas. Esta interfaz debe soportar consultas como las siguientes:

- Dado un rango entre dos fechas y un texto, obtener aquellos usuarios que incluyen en sus mensajes el texto en medio de una frase. Ordena estos usuarios por cantidad de apariciones del texto en distintos mensajes.

- Dado un rango entre dos fechas, la media de mensajes diarios para cada red social. Procura visualizar los resultados de esta consulta mediante un histograma.

- Hay que obtener una estadística de cuál es la red social dónde más se habla sobre un determinado tema. Dicho tema se definirá por un conjunto de palabras que pueden aparecer en los mensajes.
