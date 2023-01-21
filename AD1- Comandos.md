**AD1- Comandos**

1.¿Cómo sabemos si tenemos conexión a internet?

2.¿Cómo sabemos si nuestro servidor es accesible desde Internet?

3.¿Cómo sabemos a quién pertenece una dirección web (URL)?

4.¿Cómo probamos que podemos acceder a un servidor?

5.¿Qué otros comandos te han hecho falta?

*\*Nota: tener en cuenta que muchos de los comandos van a requerir permisos de administrador. En esta guía se explica cómo realizarlo en windows así que hay que iniciar la consola con permisos de administrador.*

**1. ¿Cómo sabemos si tenemos conexión a internet?**

Para saber si tenemos conexión a internet podemos seguir los siguientes pasos (véase imagen adjunta):

1. Usar el comando *IPCONFIG* en la consola de windows e *IFCONFIG* en Linux:
- De esta manera podremos tener conocimiento de la dirección IP que tenemos asignada y la puerta de enlace
- Además de la dirección IPv6 y Máscara de subred
1. Usar el comando *ping* “dirección destino” (la dirección de destino puede ser una IP o url directamente):
- Si usamos *ping* “dirección destino” (ej: ping google.es) se realizará la prueba para 4 paquetes
- Si queremos hacer ping para analizar más paquetes podemos usar el comando *ping* “dirección destino” *-t* (ej: ping google.es -t) y analizaremos todos los paquetes que queramos hasta que lo paremos usando CTRL + C
- Si obtenemos “tiempo de espera agotado para esta solicitud” quiere decir que ese paquete se ha perdido y si todos los paquetes están perdidos significa que tenemos problemas con la conexión a internet

![](/imagenes/imagen2.png)

**2. ¿Cómo sabemos si nuestro servidor es accesible desde Internet?** 

Para saber si nuestro servidor es accesible desde internet podemos usar el comando netstat, concretamente usaremos *netstat -anb* para conocer todo el listado de conexiones activas que tenemos. En nuestro caso buscaremos *httpd.exe* ya que es el servicio de Apache y comprobaremos que está en Estado:LISTENING

![](/imagenes/imagen3.png)

![](/imagenes/imagen4.png)



**3. ¿Cómo sabemos a quién pertenece una dirección web (URL)?**

Lo primero que hay que saber es que la propiedad de una dirección web (URL) se determina mediante el registro del dominio correspondiente. Cuando una persona o empresa crea un sitio web, debe registrar un nombre de dominio único a través de un registrador de dominios acreditado. Este registro les da derecho a usar ese nombre de dominio como parte de su dirección web. La información de registro del dominio, incluyendo el nombre y la dirección del propietario, se mantienen en una base de datos pública llamada Whois, que puede ser consultada para verificar quién es el propietario de un dominio específico.

Por tanto para saber a quién pertenece una dirección web (URL) podemos usar el comando *nslookup* (name server lookup) para consultar la información DNS (Domain Name System). Puede utilizarse para obtener información sobre un dominio específico, como la dirección IP asociada, el servidor de nombres autoritativo y los registros MX (Mail eXchange) utilizados para el correo electrónico.

Ejemplos de cómo usar nslookup:

- Obtener la dirección IP de un dominio específico:

nslookup example.com

- Obtener el servidor de nombres autoritativo de un dominio:

nslookup -type=ns example.com

- Obtener los registros MX de un dominio:

nslookup -type=mx example.com

- Consultar un servidor de nombres específico:

nslookup example.com 8.8.8.8

- Consultar una dirección IP específica:

nslookup 8.8.8.8

Es importante tener en cuenta que el comando nslookup es antiguo y que se está dejando de usar en favor de otras como *dig* o *hos*t.

![](/imagenes/imagen5.png)




**4.¿Cómo probamos que podemos acceder a un servidor?**

Para probar si se puede acceder a un servidor utilizando wget, podemos utilizar el comando *wget* seguido de la dirección URL del servidor que deseas probar. Por ejemplo: *wget http://www.ejemplo.com*

Si el servidor es accesible, wget descargará el contenido de la página principal de ese servidor en la carpeta actual. Si el servidor no es accesible, wget devolverá un mensaje de error indicando que no se puede conectar al servidor.

También podemos utilizar la opción "-t" para especificar el número de reintentos en caso de fallos de conexión. Por ejemplo *wget -t 3 http://www.ejemplo.com*

Este comando intentará conectarse al servidor tres veces antes de devolver un mensaje de error. Otra opción es utilizar la opción "-O" para guardar el archivo descargado con un nombre específico: *wget -O archivo.html http://www.ejemplo.com*

En resumen,  con wget podemos descargar archivos de un servidor a través de la consola de comandos y también podemos utilizarla para probar si se puede acceder a un servidor específico.

![](/imagenes/imagen6.png)

*\*Nota: es necesario instalar WGET y añadir la variable de entorno para poder usarlo desde la consola*


**5.¿Qué otros comandos te han hecho falta?**

Para la realización de la guía no tuve la necesidad de utilizar otros comandos que no vinieran en las pistas, lo que sí he usado opciones que proporcionan los comandos que se pueden consultar desde la consola (ejemplo: wget --help) o en la documentación que se puede encontrar en internet.

- ipconfig https://learn.microsoft.com/es-es/windows-server/administration/windows-commands/ipconfig
- netstat https://learn.microsoft.com/es-es/windows-server/administration/windows-commands/netstat
- nslookup <https://learn.microsoft.com/es-es/windows-server/administration/windows-commands/nslookup>
- wget https://www.hostinger.es/tutoriales/usar-comando-wget/


