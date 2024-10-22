---
title: "Creando una Aplicación Simple"
url: /es/androidjava/creando-aplicacion-simple/
weight: 10
type: docs
---

## **Cómo usar Aspose.Email para Android a través de Java**
Este tema te guiará a través de los pasos necesarios para configurar Aspose.Email para Android a través de Java en el IDE de Android Studio, asumiendo que ya tienes instalada la última versión de Android Studio en tu máquina y que también has adquirido la última versión del paquete Aspose.Email para Android a través de Java.

{{% alert color="primary" %}} 

Si aún no has instalado Android Studio, primero debes adquirir el instalador de Android Studio e instalarlo en tu máquina. Puedes descargar la última versión de Android Studio desde [este enlace](https://developer.android.com/studio/index.html#win-bundle) mientras que los detalles sobre cómo instalar el IDE están disponibles [aquí](https://developer.android.com/studio/install.html).

{{% /alert %}} {{% alert color="primary" %}} 

El paquete Aspose.Email para Android a través de Java se puede descargar desde [este enlace](https://downloads.aspose.com/email/androidjava). Ten en cuenta que cada paquete de lanzamiento de Aspose.Email para Android a través de Java consiste principalmente en 2 archivos como se detalla a continuación.

- aspose-email-x.x.x.jar es el archivo de biblioteca principal que contiene todos los espacios de nombres de la API Aspose.Email para Android a través de Java.
- aspose-email-x.x.x-libs.apk es el APK que contiene el bcprov-jdk15-146.jar de terceros utilizado para las funciones de cifrado y descifrado ofrecidas por la API Aspose.Email para Android a través de Java.

{{% /alert %}} 
## **Comenzando con Aspose.Email para Android a través de Java en Android Studio**
Una vez que se carga el IDE de Android Studio, haz clic en Archivo > Nuevo > Nuevo Proyecto como se muestra a continuación.

![todo:image_alt_text](run_examples_1.png)

También puedes crear un nuevo proyecto desde la Pantalla de Bienvenida de Android Studio, como se muestra a continuación.

![todo:image_alt_text](run_examples_2.png)

A continuación, se te pedirá que especifiques el nombre de la aplicación, el dominio y la ubicación para almacenar los archivos del proyecto. Puedes elegir cambiar los valores predeterminados según tu elección o dejarlos como están, y hacer clic en Siguiente.

![todo:image_alt_text](run_examples_3.png)

En el siguiente paso, deberás especificar el Dispositivo Android en el que deseas alojar/ejecutar tu aplicación. Una vez seleccionado, haz clic en el botón Siguiente.

![todo:image_alt_text](run_examples_4.png)

Ahora necesitas seleccionar la Actividad de una lista de plantillas predefinidas. Para mantener la demostración simple, hemos seleccionado la plantilla de Actividad Vacía como se muestra a continuación.

![todo:image_alt_text](run_examples_5.png)

Haz clic en el botón Terminar en el cuadro de diálogo Personalizar la Actividad ya que mantendremos todas las configuraciones predeterminadas tal como están.

![todo:image_alt_text](run_examples_6.png)

Tan pronto como hagas clic en el botón Terminar en el paso anterior, el IDE comenzará a construir el proyecto como se muestra a continuación. Deja que termine o haz clic en el botón Cancelar.

![todo:image_alt_text](run_examples_7.png)

Ahora el proyecto se ha cargado en el IDE, sin embargo, es posible que desees cambiar la vista a Proyecto para que puedas ver la jerarquía completa de los archivos del proyecto. Para cambiar la vista, consulta la siguiente captura de pantalla.

![todo:image_alt_text](run_examples_8.png)

Después de cambiar la vista a Proyecto, encuentra y carga el archivo build.gradle en el editor y pega el siguiente fragmento como se muestra a continuación.


~~~Java

 dexOptions{

    javaMaxHeapSize "4g"

}

~~~

![todo:image_alt_text](run_examples_9.png)

A continuación, agregaremos el Jar de Aspose.Email para Android a través de Java al proyecto. Hay 2 pasos importantes como se detalla a continuación.

- Copia manualmente el Jar de Aspose.Email para Android a través de Java a la carpeta \app\libs.
- Agrega el Jar de Aspose.Email para Android a través de Java como biblioteca al módulo como se muestra a continuación.

![todo:image_alt_text](run_examples_10.png)

Se te pedirá que selecciones el módulo al que deseas agregar el Jar de Aspose.Email para Java.Android como biblioteca. Por favor, elige apropiadamente y haz clic en Aceptar.

![todo:image_alt_text](run_examples_11.png)

También necesitas agregar el archivo APK al proyecto. Debes copiar el APK a la carpeta \app\src\main\assets. Si no tienes la carpeta assets bajo la carpeta principal, puedes crear una haciendo clic derecho en el nodo principal en la vista del Proyecto. Selecciona Nuevo > Carpeta > Carpeta de Activos.

![todo:image_alt_text](run_examples_12.png)

Una vez que el APK ha sido agregado al proyecto, debe ser cargado por el proyecto. Hay 2 maneras de cargar el APK como sigue.

- Cargar el APK en una clase de aplicación personalizada utilizando el fragmento proporcionado a continuación, y registrar la clase de aplicación personalizada en el AndroidManifest.xml.


~~~Java

 LibsLoadHelper.loadLibs(this);

~~~

- Cargar el APK en el método OnCreate de MainActivity.


~~~Java

 LibsLoadHelper.loadLibs(getApplicationContext());

~~~

Ahora estamos listos para escribir el código. Para mantener la demostración fácil de entender, hemos agregado un widget de Botón al diseño y vamos a manejar su evento de clic como sigue.


~~~Java

private class TestEmail extends AsyncTask<Void, String, Boolean> 

{

    @Override

    protected Boolean doInBackground(Void... params) 

    {

        Boolean result = false;

        try 

        {

            //Crear una instancia de PersonalStorage

            com.aspose.email.PersonalStorage pst = com.aspose.email.PersonalStorage.create("newSample_out.pst", 0);

            //Crear una carpeta en la raíz del PST

            pst.getRootFolder().addSubFolder("myInbox");

            //Agregar mensaje a la carpeta recién creada

            pst.getRootFolder().getSubFolder("myInbox").addMessage(com.aspose.email.MapiMessage.fromFile("message.msg"));

        } 

        catch (Exception e) 

        {

            e.printStackTrace();

        }

        return result;

    }

}

~~~

Cuando ejecutes la aplicación utilizando el botón de reproducción en la interfaz del IDE (o usando SHIFT + F10), el emulador cargará la aplicación como se muestra a continuación.

![todo:image_alt_text](run_examples_13.png)

Hacer clic en el botón en el emulador ejecutará el código.