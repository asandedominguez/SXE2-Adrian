# Tarea 03 - Docker 01

## 1. Descarga la imagen de Alpine sin arrancarla y comprueba que la tienes. Fija la versión: no uses latest. Escoge una versión, de las disponibles en docker hub.

Para esto utiliamos la orden pull, que sirve simplemente para descargar una imagen, sin crear ni ejecutar un contenedor. Elegí la versión 3.19 de Alpine.

![1](/Capturas/1.png)

## 2. Crea un contenedor sin nombre y sin arrancarlo. ¿En qué estado queda? ¿Qué nombre le ha puesto Docker?

Con create crearemos un contenedor. Este no tendrá nombre ya que no le establecimos ninguno, y se creará a partir de la imagen indicada.

![2](/Capturas/2.png)

Para ver el estado en el que quedó este contenedor ejecutamos la orden docker ps -a. Su función es listar los contenedores del sistema. Muestra una serie de información, en la que encuentra "STATUS", que indica que está "CREATED", esto quiere decir que no se esta ejecutando, simplemente existe y se puede activar en cualquier momento.

Se le a asignado un nombre random, el que se ve en el apartado "names"

![3](/Capturas/4.png)

## 3. Crea y arranca dam_alp1 con una shell. ¿Qué opciones necesitas para poder escribir dentro?

Parta ello ejecutamos la orden "run" que en una sola línea creara y arrancará el contenedor. Le añadimos "-it" para activar el modo de escritura. "--name" para añadir el nombre. "/bin/bash" para establecer el tipo de shell con la que queremos trabajar.
Con todas estas opciones, y como vemos en la imagen ya tendremos el contenedor creado, en ejecución, y con la shell operativa para trabajar en el.

![4](/Capturas/3.png)

## 4. Desde dentro, mira qué IP tiene y si puede hacer ping a google.com.

Lanzamos el comando "ip a", y vemos que la ip establecida es las 172.17.0.2. Puede hacer sin problema el ping

![5](/Capturas/5.png)

## 5. Deja dam_alp1 funcionando sin pararlo y crea dam_alp2 igual. Con los dos en marcha, haz ping de uno a otro: por IP y por nombre. Explica cada resultado.

Vemos con "ps" que a pesar de haber salidop de la shell el contenedor sigue activo

![6](/Capturas/6.png)

Creamos e iniciamos el contenedor y hacemos ping mediante la ip y lo hace sin problemas

![7](/Capturas/7.png)

Sin embargo lo hacemos con el nombre y da un error. Los 2 contenedores estan conectados a la red de Docker, pero este tiene el DNS desconectado ya que no lo configuramos, y por tanto no tiene la capacidad para resolver nombres y da error.

![8](/Capturas/8.png)

## 6. Con los dos en marcha, averigua cuánta memoria consumen. ¿Hay un comando de Docker para eso?

Si, tenemos la orden "stats", que basicamente hace lo que menciona el enunciado, muestra en tiempo real el consumo de los contenedores.

![9](/Capturas/9.png)

Aquí vemos el consumo de ambos.

![10](/Capturas/10.png)

## 7. Sal con exit. ¿Qué les ha pasado? Repite el comando anterior: ¿qué ves ahora y por qué?

Entramos en los contenedores de nuevo con attach. Salimos con exit. Si ahora hacemos docker ps como en la imagen veremos que no hay nada, eso es porque se pararon. Ocurre al hacer un exit en la shell, no salimos, si no que pasa el contenedor a estado "exited".

![11](/Capturas/11.png)

## 8. ¿Cuánto disco has ocupado? Distingue imágenes de contenedores.

Como vemos en la foto, las imagenes ocupan 169.5MB, y los contenedores 1.169KB.

![12](/Capturas/12.png)

Para diferenciar imagenes de contenedores vamos a hacer lo que vemos en las siguiente 2 imagenes.

En la primera veremos solo las imagenes con "image ls", y veremos también lo que ocupan (aparecen otros 2 contenedores de operaciones anteriores)

![13](/Capturas/13.png)

Y aquí con "docker ps -a" nos mostrará los contenedores inactivos, y "size" enseñará el tamaño

![14](/Capturas/14.png)