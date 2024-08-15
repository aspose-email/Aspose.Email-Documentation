---
title: "Descargar y configurar Aspose.Email en PHP"
url: /es/java/download-and-configure-aspose-email-in-php/
weight: 10
type: docs
---

## **Descargar las bibliotecas necesarias**
Descargue las bibliotecas necesarias que se mencionan a continuación. Estas son las necesarias para ejecutar los ejemplos de Java para PHP de Aspose.Email.

- **Aspose:** [Componente Aspose.Email para Java](https://downloads.aspose.com/total)
- [Puente PHP/Java](http://citylan.dl.sourceforge.net/project/php-java-bridge/Binary%20package/php-java-bridge_6.2.1/php-java-bridge_6.2.1_documentation.zip)
## **Descargar ejemplos de sitios de codificación social**
Las siguientes versiones de ejemplos de ejecución están disponibles para descargar en los sitios de codificación social que se mencionan a continuación:

-----
### **GitHub**
- **Ejemplos de Java para PHP en Aspose.Email**
  - [Aspose.Email Java para PHP](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_Java_for_PHP)
### **CodePlex**
- **Ejemplos de Java para PHP en Aspose.Email**
  - [Aspose.Email Java para PHP](https://archive.codeplex.com/?p=asposeemailjavaphp)
## **Cómo configurar el código fuente en la plataforma Linux**
Siga estos sencillos pasos para abrir y extender el código fuente mientras lo usa:
## **1. Instale el servidor Tomcat**
Para instalar el servidor Tomcat, ejecute el siguiente comando en la consola de Linux. Esto instalará correctamente el servidor Tomcat.

``` actionscript3

 sudo apt-get install tomcat8

```
## **2. Descargar y configurar PHP/JavaBridge**
Para descargar los archivos binarios de PHP/JavaBridge, ejecute el siguiente comando en la consola de Linux.

``` actionscript3

  wget http://citylan.dl.sourceforge.net/project/php-java-bridge/Binary%20package/php-java-bridge_6.2.1/php-java-bridge_6.2.1_documentation.zip

```


Descomprima los archivos binarios de PHP/JavaBridge emitiendo el siguiente comando en la consola Linux.

``` actionscript3

  unzip -d php-java-bridge_6.2.1_documentation.zip

```


Esto extraerá **JavaBridge.war** archivo. Cópielo a tomcat88 **webapps** carpeta emitiendo el siguiente comando en la consola de Linux.

``` actionscript3

  sudo cp JavaBridge.war /var/lib/tomcat8/webapps/JavaBridge.war

```


Al copiar, tomcat8 creará automáticamente una nueva carpeta»**JavaBridge**«en **webapps**. Una vez creada la carpeta, asegúrate de que tu tomcat8 se esté ejecutando y, a continuación, comprueba <http://localhost:8080/JavaBridge> en el navegador, debería abrir una página predeterminada de JavaBridge.

Si aparece algún mensaje de error, instale  **FastCGI** mediante la ejecución del siguiente comando en la consola de Linux.

``` actionscript3

  sudo apt-get install php55-cgi

```

Tras instalar php5.5 cgi, reinicie el servidor tomcat8 y compruebe <http://localhost:8080/JavaBridge> de nuevo en el navegador.

If **JAVA_HOME** aparece un error y, a continuación, abre el archivo /etc/default/tomcat8 y descomenta la línea que establece JAVA_HOME. Compruebe <http://localhost:8080/JavaBridge> en el navegador nuevamente, debería venir con la página de ejemplos de PHP/JavaBridge. 
## **3. Ejemplos de configuración de Aspose.Email Java para PHP**
Clone ejemplos de PHP emitiendo los siguientes comandos dentro de la carpeta WebApps/JavaBridge. 

``` actionscript3

 $ git init&nbsp;

$ git clone [https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_Java_for_PHP]

```


## **Cómo configurar el código fuente en la plataforma Windows**
Siga los sencillos pasos a continuación para configurar Puente PHP/Java en la plataforma Windows

1. Instala PHP5 y configúralo como lo haces normalmente
2. Instale JRE 6 (Java Runtime Environment) si aún no lo tiene. Puede comprobarlo en C:\Program Files, etc. Puede descargarlo aquí. Estoy usando JRE 6 porque es compatible con PHP Java Bridge (PJB).

3. Instale Apache Tomcat 8.0. Puede descargarlo aquí

4.Download [JavaBridge.war](https://sourceforge.net/projects/php-java-bridge/files/Binary%20package/php-java-bridge_6.2.1/JavaBridgeTemplate621.war/download). Copie este archivo al directorio de aplicaciones web de tomcat.
(por ejemplo: `C:\Program Files\Apache Software Foundation\Tomcat 8.0\webapps` )

5. Reinicie el servicio apache de Tomcat.

6. Ir a <http://localhost:8080/JavaBridge/test.php> para comprobar si php funciona. Puedes encontrar otros ejemplos allí

7. Copia tu [Aspose.Email Java](https://downloads.aspose.com/total) archivo jar a `C:\Program Files\Apache Software Foundation\Tomcat 8.0\webapps\JavaBridge\WEB-INF\lib`

8. Clone [Aspose.Email Java para PHP](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose.Email-for-Java_for_PHP) ejemplos en el interior `C:\Program Files\Apache Software Foundation\Tomcat 8.0\webapps\` folder.

8. Copiar carpeta `C:\Program Files\Apache Software Foundation\Tomcat 8.0\webapps\JavaBridge\java` a su carpeta de ejemplos de Java for PHP de Aspose.Email.

\ 10. Reinicie el servicio apache tomcat y comience a usar ejemplos.
