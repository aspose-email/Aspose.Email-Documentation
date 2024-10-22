---
title: "Descargar y Configurar Aspose.Email en Ruby"
url: /es/java/download-and-configure-aspose-email-in-ruby/
weight: 10
type: docs
---


## **Descargar Bibliotecas Requeridas**
Descargue las bibliotecas requeridas mencionadas a continuación. Estas son necesarias para ejecutar ejemplos de Aspose.Email Java para Ruby.

- [Aspose.Email para Java Component](https://downloads.aspose.com/total)
## **Descargar Ejemplos de Sitios de Codificación Social**
Siguiendo lanzamientos de ejemplos en ejecución, están disponibles para descargar en los sitios de codificación social mencionados a continuación:

**GitHub**

- [Aspose.Email Java para Ruby](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_Java_for_Ruby)
## **Instalación**
Es muy simple y fácil instalar el gem de Aspose.Email Java para Ruby, por favor siga estos simples pasos:

1. Ejecute el siguiente comando.

``` java

 $ gem install aspose-emailjava

```

1. Descargue el componente requerido de Aspose.Email para Java desde el siguiente enlace.
   <https://downloads.aspose.com/total>
1. Cree una carpeta "jars" en la raíz del gem de Aspose.Email Java para Ruby y copie el componente descargado en ella.
## **Uso**
Incluya los archivos requeridos para trabajar con el ejemplo **createnewemail**.

``` java

 require File.dirname(File.dirname(File.dirname(__FILE__))) + '/lib/aspose-emailjava'

include Asposeemailjava

include Asposeemailjava::CreateNewEmail

initialize_aspose_email

```

Entendamos el código anterior.

1. La primera línea asegura que el aspose email esté cargado y disponible.
1. Incluya los archivos que son necesarios para acceder al aspose email.
1. Inicialice las bibliotecas. Las clases JAVA de aspose se cargan desde la ruta proporcionada en el archivo aspose.yml.