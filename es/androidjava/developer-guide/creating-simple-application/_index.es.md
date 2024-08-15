---
title: "Creación de una aplicación sencilla"
url: /es/androidjava/creating-simple-application/
weight: 10
type: docs
---

## **Cómo usar Aspose.Emil para Android a través de Java**
Este tema te guiará a través de los pasos necesarios para configurar Aspose.Email para Android a través de Java en el IDE de Android Studio, suponiendo que ya tienes la versión más reciente de Android Studio instalada en tu máquina y que también has adquirido la última versión de Aspose.Email para Android a través del paquete Java.

{{% alert color="primary" %}}

Si aún no has instalado Android Studio, primero tienes que adquirir la configuración de Android Studio e instalarla en tu máquina. Puedes descargar la versión más reciente de Android Studio desde [here ](https://developer.android.com/studio/index.html#win-bundle)mientras que los detalles sobre cómo instalar el IDE están disponibles [here](https://developer.android.com/studio/install.html).

{{% /alert %}} {{% alert color="primary" %}}

El paquete Aspose.Email para Android a través de Java se puede descargar desde [here](https://downloads.aspose.com/email/androidjava). Tenga en cuenta que cada paquete de lanzamiento de Aspose.Email para Android a través de Java consta principalmente de 2 archivos, como se detalla a continuación.

- aspose-email-x.x.x.jar es el archivo de biblioteca principal que contiene todos los espacios de nombres de Aspose.Email para Android a través de la API de Java.
- aspose-email-x.x.x-libs.apk es el APK que contiene el archivo bcprov-jdk15-146.jar de terceros que se utiliza para las funciones de cifrado y descifrado que ofrece Aspose.Email para Android a través de la API de Java.

{{% /alert %}}
## **Primeros pasos con Aspose.Email para Android a través de Java en Android Studio**
Una vez que se cargue el IDE de Android Studio, haz clic en Archivo > Nuevo > Nuevo proyecto, como se muestra a continuación.

![todo:image_alt_text](run_examples_1.png)

También puedes crear un nuevo proyecto desde la pantalla de bienvenida de Android Studio, como se muestra a continuación.

![todo:image_alt_text](run_examples_2.png)

A continuación, se le pedirá que especifique el nombre de la aplicación, el dominio y la ubicación para almacenar los archivos del proyecto. Puede elegir cambiar los valores predeterminados según su elección o dejarlos como están y hacer clic en Siguiente.

![todo:image_alt_text](run_examples_3.png)

En el siguiente paso, debe especificar el dispositivo Android en el que desea alojar/ejecutar su aplicación. Una vez seleccionado, haga clic en el botón Siguiente.

![todo:image_alt_text](run_examples_4.png)

Ahora tiene que seleccionar la actividad de una lista predefinida de plantillas. Para que la demostración sea sencilla, hemos seleccionado la plantilla de actividad vacía como se muestra a continuación.

![todo:image_alt_text](run_examples_5.png)

Haga clic en el botón Finalizar en el cuadro de diálogo Personalizar la actividad, ya que mantendremos todos los ajustes predeterminados tal como están.

![todo:image_alt_text](run_examples_6.png)

Tan pronto como hagas clic en el botón Finalizar del paso anterior, el IDE comenzará a crear el proyecto como se muestra a continuación. Deja que termine o haz clic en el botón Cancelar.

![todo:image_alt_text](run_examples_7.png)

Ahora que el proyecto se ha cargado en el IDE, sin embargo, es posible que desee cambiar la vista a Project para poder ver la jerarquía completa de los archivos del proyecto. Para cambiar la vista, compruebe la siguiente instantánea.

![todo:image_alt_text](run_examples_8.png)

Tras cambiar la vista a Project, busca y carga el archivo build.gradle en el editor y pega el siguiente fragmento como se muestra a continuación.


~~~Java

 dexOptions{

    javaMaxHeapSize "4g"

}

~~~

![todo:image_alt_text](run_examples_9.png)

A continuación, agregaremos Aspose.Email para Android a través de Java Jar al proyecto. Hay 2 pasos importantes que se detallan a continuación.

- Copie manualmente el archivo Aspose.Email para Android a través de Java Jar a la carpeta\ app\ libs.
- Agregue Aspose.Email para Android a través de Java Jar como biblioteca al módulo como se muestra a continuación.

![todo:image_alt_text](run_examples_10.png)

Se le pedirá que seleccione el módulo al que desea agregar Aspose.Email for Java.Android Jar como biblioteca. Elija la opción adecuada y haga clic en Aceptar.

![todo:image_alt_text](run_examples_11.png)

También tienes que añadir el archivo APK al proyecto. Tienes que copiar el APK a la carpeta\ app\ src\ main\ assets. Si no tiene la carpeta de activos en la carpeta principal, puede crear una haciendo clic con el botón derecho en el nodo principal de la vista de proyecto. Seleccione Nuevo > Carpeta > Carpeta de activos.

![todo:image_alt_text](run_examples_12.png)

Una vez que se haya agregado el APK al proyecto, el proyecto debe cargarlo. Hay dos formas de cargar el APK de la siguiente manera.

- Cargue el APK en una clase de aplicación personalizada mediante el fragmento que se proporciona a continuación y registre la clase de aplicación personalizada en el archivo AndroidManifest.xml.


~~~Java

 LibsLoadHelper.loadLibs(this);

~~~

- Carga el APK en el método onCreate de MainActivity.


~~~Java

 LibsLoadHelper.loadLibs(getApplicationContext());

~~~

Ahora estamos listos para escribir el código. Para que la demostración sea fácil de entender, hemos añadido un widget de botones al diseño y vamos a gestionar su evento de clic de la siguiente manera.


~~~Java

private class TestEmail extends AsyncTask<Void, String, Boolean>

{

    @Override

    protected Boolean doInBackground(Void... params)

    {

        Boolean result = false;

        try

        {

            //Create an instance of PersonalStorage

            com.aspose.email.PersonalStorage pst = com.aspose.email.PersonalStorage.create("newSample_out.pst", 0);

            //Create a folder at root of PST

            pst.getRootFolder().addSubFolder("myInbox");

            //Add message to newly created folder

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

Cuando ejecutas la aplicación con el botón de reproducción de la interfaz IDE (o con SHIFT + F10), el emulador cargará la aplicación como se muestra a continuación.

![todo:image_alt_text](run_examples_13.png)

Al hacer clic en el botón del emulador, se ejecutará el código.
