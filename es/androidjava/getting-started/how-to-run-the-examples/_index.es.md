---
title: "Cómo ejecutar los ejemplos"
url: /es/androidjava/how-to-run-the-examples/
weight: 70
type: docs
---

## **Descargar desde GitHub**
Todos los ejemplos de Aspose.Email para Java están alojados en [Github](https://github.com/aspose-email/Aspose.Email-for-Java). Puedes clonar el repositorio usando tu cliente Github favorito o descargar el archivo ZIP desde [here](https://forum.aspose.com/c/email/12).

Extraiga el contenido del archivo ZIP a cualquier carpeta de su computadora. Todos los ejemplos se encuentran en el **Examples** folder.

![todo:image_alt_text](https://i.imgur.com/WsQ2wrb.png)

El proyecto utiliza el sistema de construcción Maven. Cualquier IDE moderno puede abrir o importar fácilmente el proyecto y sus dependencias. A continuación, le mostramos cómo usar los IDE más populares para crear y ejecutar los ejemplos.

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

Ahora estamos listos para usar el código del archivo Examples.

## **Contribute**
Si quieres añadir o mejorar un ejemplo, te animamos a que contribuyas al proyecto. Todos los ejemplos y proyectos destacados de este repositorio son de código abierto y se pueden usar libremente en tus propias aplicaciones.

Para contribuir, puedes bifurcar el repositorio, editar el código fuente y crear una solicitud de cambios. Revisaremos los cambios y los incluiremos en el repositorio si los consideramos útiles.
