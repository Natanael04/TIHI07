# TIHI07
<h1>Trabajo CentOS7
  <h2>Introduccion</h2>
  Con el presente repositorio crearemos una guia la cual contiene los siguientes puntos:
  
  &nbsp;
  
  1. Instalacion de una ISO en VirtualBox en esta oportunidad usaremos **CentOS7**
  1. Habilitar SSH
  1. Instalacion de Java Oracle
  1. Instalacion de un ambiente o interfaz de escritorio
  1. Instalacion de un IDE **(NetBeans)**
  1. Instalacion de una base de datos **(PostgreSQL)**
  1. Test de Java, utilizando un framework
  1. Comprobacion de conexion a la base de datos

  &nbsp;
  
  <h3>1.- Instalacion ISO CentOS7 en VirtualBox</h3>
  
  &nbsp;
  
   En primer lugar bajaremos el ISO desde la pagina principal https://www.centos.org/download/. Nos dirigimos a **Minimal ISO** para esta oportunidad descargaremos la primera opcion.

&nbsp;

 <h3>2.- Habilitacion de SSH</h3>
 
&nbsp;

 En la linea de comandos escribiremos lo siguiente :
 
      yum -y install openssh-server openssh-clients 
      
 Este comando nos permite instalar el servidor y cliente.
 
 &nbsp;
 
 Una vez ya instalado lo habilitamos con el siguiente comando : 
 
      chkconfig sshd on
 
&nbsp;

Posteriormente cerramos la máquina para configurar el puerto de conexión desde el menú de configuración en virtualbox. Este será a través del puerto 8001 con la ip por defecto de nuestra maquina local, la cual es 17.0.0.1

Levantamos la interfaz de red de nombre “enp0s3” con el comando:

      Ifup enp0s3
      
Nos dirigimos a Putty e ingresamos la IP y puertos definidos anteriormente, cuando la conexión es exitosa nos pedirá el usuario y contraseña de la máquina virtual, una vez ingresado este usuario tendremos control de la máquina virtual a través de la consola de comandos de Putty.
 
&nbsp;

<h3>3.- Instalacion de Java Oracle</h3>

Primero nos dirigimos a la página oficial de java https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html y en esta buscaremos la descarga del JDK que termina en “.rpm”, una vez identificado el link de descarga lo colocaremos en conjunto al siguiente comando:

      wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" "(En este espacio se coloca el link de descarga)" 
      
&nbsp;

<img src="https://github.com/Natanael04/TIHI07/blob/master/Informe/descargar%20oracle%20JDK%208.png" width="" height="">


Para instalar el archivo descargado escribiremos lo siguiente:

      yum localinstall jdk-8u161-linux-x64.rpm
      
 &nbsp;
 
 <img src="" width="" height="">
      
A medida que instala nos pedirá la confirmación por lo que aceptaremos con la letra “y”
Para dejar de default nuestro java escribiremos las siguientes líneas de comando:

      java –versión
      
      sudo alternatives --config java 
      
Colocado el segundo comando nos saldrá la lista de los JDK o JRE existentes y nos marcara el por defecto con un “+” y definidos por una numeración, por lo que colocaremos el número del JDK instalado para asignarlo por defecto.

&nbsp;

<h3>4.-  Instalación de un ambiente o interfaz (Gnome).</h3>

Primero abrimos una ventana terminal e introducimos el siguiente comando 

      sudo add-apt-repository ppa: gnome3-team / gnome3
      
Para instalar ejecutaremos el siguiente comando:

      sudo apt-get update && sudo apt-get install gnome-shell ubuntu-gnome-desktop
      
Continuado con esto seleccionamos el administrador de inicio de sesión, cuando finalice la instalación, cerramos el terminal y reiniciamos el sistema.

&nbsp;

<h3>5.-  Instalación de un IDE (NetBeans).</h3>

Para instalar este IDE abrimos una ventana terminal en la cual escribiremos lo siguiente: 

      wget -c http://download.netbeans.org/netbeans/8.2/final/bundles/netbeans-8.2-linux.sh 
      
Completada la descargar ejecutamos el siguiente commando para hacer ejecutable el scrip del instalador y comenzar a instalar: 

      chmod + x netbeans-8.2-linux.sh
      
      ./netbeans-8.2-linux.sh
      
Luego seguimos la instalación normal y ya tendríamos instalado el NetBeans. 

&nbsp;

<h3>6.-  Instalacion de PostGreSQL.</h3>

Para instalar PostGreSQL abrimos una ventana terminal en la cual copiaremos el siguiente comando: 
 
       yum install postgresql96 postgresql96-server postgresql96-contrib postgresql96-libs –y
       
Para Inicializar escribiremos lo siguiente:

      /usr/pgsql-9.6/bin/postgresql96-setup initdb 
      
Ahora Iniciamos y Habilitamos PostGreSQL: 

      systemctl enable postgresql-9.6.service 
      
      systemctl start postgresql-9.6.service 
      
