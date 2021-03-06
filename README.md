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
  1. Comprobacion de conexion a la base de datos

  &nbsp;
  
  <h3>1.- Instalacion ISO CentOS7 en VirtualBox</h3>
  
  &nbsp;
  
   En primer lugar bajaremos el ISO desde la pagina principal https://www.centos.org/download/. Nos dirigimos a **Minimal ISO** para esta oportunidad descargaremos la primera opcion.
   
 <img src="https://github.com/Natanael04/TIHI07/blob/master/Informe/Descarga%20CentOS7.png" width="" height="">
   
   Posteriormente, en la maquina virtual montaremos el ISO descargado

<img src="https://github.com/Natanael04/TIHI07/blob/master/Informe/abrir%20OS.png" width="" height="">

&nbsp;

 <h3>2.- Habilitacion de SSH</h3>
 
&nbsp;

 En la linea de comandos escribiremos lo siguiente :
 
      yum -y install openssh-server openssh-clients 
      
 <img src="https://github.com/Natanael04/TIHI07/blob/master/Informe/Cliente-Servidor.png" width="" height="">
   
 
 Este comando nos permite instalar el servidor y cliente.
 
 &nbsp;
 
 Una vez ya instalado lo habilitamos con el siguiente comando : 
 
      chkconfig sshd on
 
 <img src="https://github.com/Natanael04/TIHI07/blob/master/Informe/chkconfig.png" width="" height="">
 
&nbsp;

Posteriormente cerramos la máquina para configurar el puerto de conexión desde el menú de configuración en virtualbox. Este será a través del puerto 8001 con la ip por defecto de nuestra maquina local, la cual es 17.0.0.1 en el apartado "Red/Reenvio de puertos"

<img src="https://github.com/Natanael04/TIHI07/blob/master/Informe/Reenvio%20de%20puertos.png" width="" height="">

Levantamos la interfaz de red de nombre “enp0s3” con el comando:

      Ifup enp0s3
      
<img src="https://github.com/Natanael04/TIHI07/blob/master/Informe/ifup%20enp0s3.png" width="" height="">
      
Nos dirigimos a Putty e ingresamos la IP y puertos definidos anteriormente, cuando la conexión es exitosa nos pedirá el usuario y contraseña de la máquina virtual, una vez ingresado este usuario tendremos control de la máquina virtual a través de la consola de comandos de Putty.
 
 <img src="https://github.com/Natanael04/TIHI07/blob/master/Informe/Putty.png" width="" height="">
 
&nbsp;

<h3>3.- Instalacion de Java Oracle</h3>

Primero nos dirigimos a la página oficial de java https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html y en esta buscaremos la descarga del JDK que termina en “.rpm”, una vez identificado el link de descarga lo colocaremos en conjunto al siguiente comando:

      wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" "(En este espacio se coloca el link de descarga)" 
      
&nbsp;

<img src="https://github.com/Natanael04/TIHI07/blob/master/Informe/descargar%20oracle%20JDK%208.png" width="" height="">


Para instalar el archivo descargado escribiremos lo siguiente:

      yum localinstall jdk-8u161-linux-x64.rpm
      
 &nbsp;
 
 <img src="https://github.com/Natanael04/TIHI07/blob/master/Informe/instalar%20oracle%20JDK8.png" width="" height="">
      
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



Posteriormente seleccionamos el administrador de inicio de sesión, cuando finalice la instalación, cerramos el terminal y reiniciamos el sistema.

<img src="https://github.com/Natanael04/TIHI07/blob/master/Informe/Gnome.png" width="" height="">

&nbsp;

<h3>5.-  Instalación de un IDE (NetBeans).</h3>

Para instalar este IDE abrimos una ventana terminal en la cual escribiremos lo siguiente: 

      wget -c http://download.netbeans.org/netbeans/8.2/final/bundles/netbeans-8.2-linux.sh 
      
Completada la descargar ejecutamos el siguiente commando para hacer ejecutable el scrip del instalador y comenzar a instalar: 

      chmod + x netbeans-8.2-linux.sh
      
      ./netbeans-8.2-linux.sh
<img src="https://github.com/Natanael04/TIHI07/blob/master/Informe/InstaladorN.png" width="" height="">

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

&nbsp;
<h3>7.-  Comprobacion de conexion a la base de datos.</h3>

Una vez abierto NetBeans crearemos un proyecto nuevo, en nuestro proyecto iremos a la carpeta **Project Files**, y abriremos el archivo pom.xml

En este archivo bajaremos las dependencias que necesita PostGre, en el cual escribiremos los siguientes codigos:

      <dependencies>
        <dependency>
        <groupId>org.postgresql</groupId>
        <artifactId>postgresql</artifactId>
        <version>42.2.5</version>
        </dependency>
      </dependencies>
      
Despues que baje lo requerido crearemos otro proyecto de nombre test, en este proyecto crearemos un main en el cual escribiremos lo siguiente: 

      import java.sql.Connection;
      import java.sql.DriverManager;
      import java.sql.ResultSet;
      import java.sql.SQLException;
      import java.sql.Statement;

      /**
       * @author imssbora
       */
      public class JDBCExample {
        public static void main(String[] args) {

    String jdbcUrl = "jdbc:postgresql://localhost:5432/"nombre de base de datos";
    String username = "Usuario";
    String password = "Contraseña";

    Connection conn = null;
    Statement stmt = null;
    ResultSet rs = null;

    try {
 
      conn = DriverManager.getConnection(jdbcUrl, username, password);


      stmt = conn.createStatement();
      rs = stmt.executeQuery("SELECT version()");


      if (rs.next()) {
        System.out.println(rs.getString(1));
      }

    } catch (SQLException e) {
      e.printStackTrace();

    } finally {
      try {

        if (stmt != null) {
          stmt.close();
        }
        if (rs != null) {
          rs.close();
        }
        if (conn != null) {
          conn.close();
        }
      } catch (Exception e) {
        e.printStackTrace();
      }
    }

        }
      }

(Para que nos arranque debemos importar la libreria de SQL)

finalmente al arrancar el proyecto nos imprimira la version y no nos arrojara error quedandonos lo siguiente: 

<img src="https://github.com/Natanael04/TIHI07/blob/master/Informe/postgreconn.png" width="" height="">
