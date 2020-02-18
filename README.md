# SocketHospital
Práctica de Sockets siguiendo un protocolo dado.

ENUNCIADO DEL EJERCICIO
 
  El equipo de directivo de la empresa para la que trabajamos ha contactado con el gerente de un hospital y ha llegado a un acuerdo para que seamos nosotros los que implementemos una aplicación que permita su gestión. Entre otros muchos servicios la empresa oferta la posibilidad de gestionar los ingresos hospitalarios (Expediente, paciente, médico y tratamiento).
Aunque actualmente el hospital sólo tiene una sede en un futuro sí tiene pensado ampliar sus servicios a través de una red de centros de salud. Por eso se estima que lo mejor es tener un servidor donde se almacene toda la información y que cada sede se conecte a éste para enviar y recibir los datos.
El proceso que hará las veces de cliente se conectará al servidor para enviar y recibir los comandos correspondientes a la gestión de creación, eliminación y recuperación de los datos de expedientes, pacientes).

Protocolo a implementar:
El protocolo de comunicación entre cliente y servidor establece la arquitectura del sistema así como los comandos necesarios para su gestión.
También cuenta con un control de acceso (usuario y contraseña). De tal forma que sólo los usuarios registrados pueden acceder a toda la funcionalidad de la aplicación. Para simplificar dicho funcionamiento sólo se utilizará el usuario admin con clave admin.
En cuanto a la arquitectura destacar que se trata de un protocolo de tipo petición-respuesta y que tiene dos canales de comunicación, uno para comandos y otro para datos. El primer canal trabaja sobre el puerto 2019 mientras que el canal de envío de datos lo hace sobre el 2020 y sucesivos.
Cada envío/mensaje enviado por el cliente hacia el servidor está identificado por un texto alfanumérico <number> (números, letras o números y letras). No se trata de un identificador del comando sino del envío en sí. 
Todo comando enviado tendrá una respuesta por parte del servidor. En dicha respuesta se incluirá el <number> que envió el cliente, el código de respuesta y el resultado de la operación: OK ó FAIL.

La creación del canal de datos se realiza siempre de la misma manera:
1. El cliente envía un comando que necesita de transmisión de datos.
2. El servidor envía como respuesta a través del canal de comandos la ip y el puerto al que debe conectarse. Para ello tendrá un listado de puertos disponibles (del 2020 en adelante) y cogerá uno para crear el ServerSocket correspondiente. 
3. El servidor se pone a la escucha serverSocket.accept(). 
4. El cliente lanza una petición de conexión, new Socket(ip,puerto), a la ip y el puerto que el servidor le indicó. 
5. Se procede al envío y recepción del objeto solicitado.
