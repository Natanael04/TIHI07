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
    
*aca tiene que ir como se instala la iso y la config del virtual box*

&nbsp;

 <h3>2.- Habilitacion de SSH</h3>
 
&nbsp;
*aca va la descarga del putty y las confg*

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

      
