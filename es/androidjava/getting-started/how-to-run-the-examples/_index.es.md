---
title: "Cómo Ejecutar los Ejemplos"
url: /es/androidjava/how-to-run-the-examples/
weight: 70
type: docs
---

## **Descargar desde GitHub**
Todos los ejemplos de Aspose.Email para Java están alojados en [Github](https://github.com/aspose-email/Aspose.Email-for-Java). Puedes clonar el repositorio usando tu cliente de Github favorito o descargar el archivo ZIP desde [aquí](https://forum.aspose.com/c/email/12).

Extrae el contenido del archivo ZIP a cualquier carpeta en tu computadora. Todos los ejemplos se encuentran en la carpeta **Examples**.

![todo:image_alt_text](https://i.imgur.com/WsQ2wrb.png)

El proyecto utiliza el sistema de construcción Maven. Cualquier IDE moderno puede abrir o importar fácilmente el proyecto y sus dependencias. A continuación, te mostramos cómo usar IDEs populares para construir y ejecutar los ejemplos.

## **Cómo usar Aspose.Email para Android a través de Java**
Este tema te guiará a través de los pasos necesarios para configurar Aspose.Email para Android a través de Java en Android Studio IDE, asumiendo que ya tienes instalada la última versión de Android Studio en tu máquina y que también has adquirido la última versión del paquete Aspose.Email para Android a través de Java.

{{% alert color="primary" %}} 

Si aún no has instalado Android Studio, primero debes adquirir la configuración de Android Studio e instalarla en tu máquina. Puedes descargar la última versión de Android Studio desde [aquí](https://developer.android.com/studio/index.html#win-bundle), mientras que los detalles sobre cómo instalar el IDE están disponibles [aquí](https://developer.android.com/studio/install.html).

{{% /alert %}} {{% alert color="primary" %}} 

El paquete Aspose.Email para Android a través de Java se puede descargar desde [aquí](https://downloads.aspose.com/email/androidjava). Ten en cuenta que cada paquete de lanzamiento de Aspose.Email para Android a través de Java consta principalmente de 2 archivos, como se detalla a continuación.

- aspose-email-x.x.x.jar es el archivo de biblioteca principal que contiene todos los espacios de nombres de la API de Aspose.Email para Android a través de Java.
- aspose-email-x.x.x-libs.apk es el APK que contiene el bcprov-jdk15-146.jar de terceros utilizado para las funciones de cifrado y descifrado ofrecidas por la API de Aspose.Email para Android a través de Java.

{{% /alert %}} 
## **Introducción a Aspose.Email para Android a través de Java en Android Studio**
Una vez que se carga el IDE de Android Studio, haz clic en Archivo > Nuevo > Nuevo Proyecto como se muestra a continuación.

![todo:image_alt_text](run_examples_1.png)

También puedes crear un nuevo proyecto desde la Pantalla de Bienvenida de Android Studio como se muestra a continuación.

![todo:image_alt_text](run_examples_2.png)

A continuación, se te pedirá que especifiques el nombre de la aplicación, el dominio y la ubicación para almacenar los archivos del proyecto. Puedes optar por cambiar los valores predeterminados según tu elección o dejarlos como están, y hacer clic en Siguiente.

![todo:image_alt_text](run_examples_3.png)

En el siguiente paso, debes especificar el Dispositivo Android en el que deseas alojar/ejecutar tu aplicación. Una vez seleccionado, haz clic en el botón Siguiente.

![todo:image_alt_text](run_examples_4.png)

Ahora necesitas seleccionar la Actividad de una lista de plantillas predefinidas. Para mantener la demostración simple, hemos seleccionado la plantilla de Actividad Vacía como se muestra a continuación.

![todo:image_alt_text](run_examples_5.png)

Haz clic en el botón Finalizar en el diálogo Personalizar la Actividad ya que mantendremos todas las configuraciones predeterminadas como están.

![todo:image_alt_text](run_examples_6.png)

Tan pronto como hagas clic en el botón Finalizar en el paso anterior, el IDE comenzará a construir el proyecto como se muestra a continuación. Deja que termine o haz clic en el botón Cancelar.

![todo:image_alt_text](run_examples_7.png)

Ahora el proyecto ha sido cargado en el IDE, sin embargo, es posible que desees cambiar la vista a Proyecto para que puedas ver la jerarquía completa de los archivos del proyecto. Para cambiar la vista, consulta la siguiente captura de pantalla.

![todo:image_alt_text](run_examples_8.png)

Después de cambiar la vista a Proyecto, busca y carga el archivo build.gradle en el editor y pega el siguiente fragmento como se muestra a continuación.

~~~Java

 dexOptions{

    javaMaxHeapSize "4g"

}

~~~

![todo:image_alt_text](run_examples_9.png)

A continuación, agregaremos el Jar de Aspose.Email para Android a través de Java al proyecto. Hay 2 pasos importantes, como se detalla a continuación.

- Copia manualmente el Jar de Aspose.Email para Android a través de Java a la carpeta \app\libs.
- Agrega el Jar de Aspose.Email para Android a través de Java como Biblioteca al módulo como se muestra a continuación.

![todo:image_alt_text](run_examples_10.png)

Se te pedirá que selecciones el módulo al que deseas agregar el Jar de Aspose.Email para Java.Android como biblioteca. Por favor elige apropiadamente y haz clic en Aceptar.

![todo:image_alt_text](run_examples_11.png)

También necesitas agregar el archivo APK al proyecto. Debes copiar el APK a la carpeta \app\src\main\assets. Si no tienes la carpeta assets bajo la carpeta principal, puedes crear una haciendo clic derecho en el nodo principal en la vista del Proyecto. Selecciona Nuevo > Carpeta > Carpeta de Activos.

![todo:image_alt_text](run_examples_12.png)

Una vez que el APK se haya agregado al proyecto, necesita ser cargado por el proyecto. Hay 2 formas de cargar el APK como sigue.

- Carga el APK en una clase de aplicación personalizada utilizando el fragmento proporcionado a continuación y registra la clase de aplicación personalizada en el AndroidManifest.xml.

~~~Java

 LibsLoadHelper.loadLibs(this);

~~~

- Carga el APK en el método OnCreate de MainActivity.

~~~Java

 LibsLoadHelper.loadLibs(getApplicationContext());

~~~

Ahora estamos listos para usar el código del archivo de ejemplos.

## **Contribuir**
Si deseas agregar o mejorar un ejemplo, te animamos a contribuir al proyecto. Todos los ejemplos y proyectos de demostración en este repositorio son de código abierto y se pueden usar libremente en tus propias aplicaciones.

Para contribuir, puedes bifurcar el repositorio, editar el código fuente y crear una solicitud de extracción. Revisaremos los cambios e incluirlos en el repositorio si se considera útil.