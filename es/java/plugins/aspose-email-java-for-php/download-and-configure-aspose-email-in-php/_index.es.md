---
title: "Descargar y Configurar Aspose.Email en PHP"
url: /es/java/download-and-configure-aspose-email-in-php/
weight: 10
type: docs
---

## **Descargar Librerías Requeridas**
Descargue las librerías requeridas mencionadas a continuación. Estas son necesarias para ejecutar ejemplos de Aspose.Email Java para PHP.

- **Aspose:** [Aspose.Email para Componente Java](https://downloads.aspose.com/total)
- [PHP/Java Bridge](http://citylan.dl.sourceforge.net/project/php-java-bridge/Binary%20package/php-java-bridge_6.2.1/php-java-bridge_6.2.1_documentation.zip)
## **Descargar Ejemplos de Sitios de Programación Social**
Las siguientes versiones de ejemplos en ejecución están disponibles para descargar en los sitios de programación social mencionados a continuación:

-----
### **GitHub**
- **Ejemplos de Aspose.Email Java para PHP**
  - [Aspose.Email Java para PHP](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_Java_for_PHP)
### **CodePlex**
- **Ejemplos de Aspose.Email Java para PHP**
  - [Aspose.Email Java para PHP](https://archive.codeplex.com/?p=asposeemailjavaphp)
## **Cómo configurar el código fuente en la Plataforma Linux**
Siga estos sencillos pasos para abrir y extender el código fuente mientras usa:
## **1. Instalar el Servidor Tomcat**
Para instalar el servidor Tomcat, emita el siguiente comando en la consola de Linux. Esto instalará exitosamente el servidor Tomcat.

``` actionscript3

 sudo apt-get install tomcat8

```
## **2. Descargar y Configurar PHP/JavaBridge**
Para descargar los binarios de PHP/JavaBridge, emita el siguiente comando en la consola de Linux.

``` actionscript3

  wget http://citylan.dl.sourceforge.net/project/php-java-bridge/Binary%20package/php-java-bridge_6.2.1/php-java-bridge_6.2.1_documentation.zip 

```


Descomprima los binarios de PHP/JavaBridge emitiendo el siguiente comando en la consola de Linux.

``` actionscript3

  unzip -d php-java-bridge_6.2.1_documentation.zip 

```


Esto extraerá el archivo **JavaBridge.war**. Copie este archivo a la carpeta **webapps** de tomcat88 emitiendo el siguiente comando en la consola de Linux.

``` actionscript3

  sudo cp JavaBridge.war /var/lib/tomcat8/webapps/JavaBridge.war 

```


Al copiar, tomcat8 creará automáticamente una nueva carpeta "**JavaBridge**" en **webapps**. Una vez creada la carpeta, asegúrese de que su tomcat8 esté en funcionamiento y luego verifique <http://localhost:8080/JavaBridge> en el navegador; esto debería abrir una página predeterminada de JavaBridge.

Si aparece algún mensaje de error, entonces instale **FastCGI** emitiendo el siguiente comando en la consola de Linux.

``` actionscript3

  sudo apt-get install php55-cgi 

```

Después de instalar php5.5 cgi, reinicie el servidor tomcat8 y verifique <http://localhost:8080/JavaBridge> nuevamente en el navegador.

Si se muestra un error de **JAVA_HOME**, entonces abra el archivo /etc/default/tomcat8 y descomente la línea que establece JAVA_HOME. Verifique <http://localhost:8080/JavaBridge> en el navegador nuevamente, esto debería mostrar la página de Ejemplos de PHP/JavaBridge. 
## **3. Configurar Ejemplos de Aspose.Email Java para PHP**
Clone los ejemplos de PHP emitiendo los siguientes comandos dentro de la carpeta webapps/JavaBridge. 

``` actionscript3

 $ git init&nbsp;

$ git clone [https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_Java_for_PHP] 

```


## **Cómo configurar el código fuente en la Plataforma Windows**
Siga los siguientes pasos sencillos para configurar PHP/Java Bridge en la Plataforma Windows:

1. Instale PHP5 y configúrelo como normalmente lo hace.
2. Instale JRE 6 (Java Runtime Environment) si aún no lo tiene. Puede verificar esto en C:\Program Files, etc. Puede descargarlo aquí. Estoy usando JRE 6 ya que es compatible con PHP Java Bridge (PJB).

3. Instale Apache Tomcat 8.0. Puede descargarlo aquí.

4. Descargue [JavaBridge.war](https://sourceforge.net/projects/php-java-bridge/files/Binary%20package/php-java-bridge_6.2.1/JavaBridgeTemplate621.war/download). Copie este archivo en el directorio webapps de tomcat.
(ex: `C:\Program Files\Apache Software Foundation\Tomcat 8.0\webapps` )

5. Reinicie el servicio apache tomcat.

6. Vaya a <http://localhost:8080/JavaBridge/test.php> para verificar si php funciona. Puede encontrar otros ejemplos allí.

7. Copie su archivo jar de [Aspose.Email Java](https://downloads.aspose.com/total) a `C:\Program Files\Apache Software Foundation\Tomcat 8.0\webapps\JavaBridge\WEB-INF\lib`.

8. Clone los ejemplos de [Aspose.Email Java para PHP](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose.Email-for-Java_for_PHP) dentro de la carpeta `C:\Program Files\Apache Software Foundation\Tomcat 8.0\webapps\`.

9. Copie la carpeta `C:\Program Files\Apache Software Foundation\Tomcat 8.0\webapps\JavaBridge\java` a su carpeta de ejemplos de Aspose.Email Java para PHP.

10. Reinicie el servicio apache tomcat y comience a usar los ejemplos.