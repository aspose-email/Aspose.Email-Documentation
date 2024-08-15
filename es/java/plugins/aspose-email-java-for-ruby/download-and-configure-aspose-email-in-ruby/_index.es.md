---
title: "Descargar y configurar Aspose.Email en Ruby"
url: /es/java/download-and-configure-aspose-email-in-ruby/
weight: 10
type: docs
---


## **Descargar las bibliotecas necesarias**
Descargue las bibliotecas necesarias que se mencionan a continuación. Estas son las necesarias para ejecutar los ejemplos de Java for Ruby de Aspose.Email.

- [Componente Aspose.Email para Java](https://downloads.aspose.com/total)
## **Descargar ejemplos de sitios de codificación social**
Las siguientes versiones de ejemplos de ejecución están disponibles para descargar en los sitios de codificación social que se mencionan a continuación:

**GitHub**

- [Aspose.Email Java para Ruby](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_Java_for_Ruby)
## **Installing**
La gema Aspose.Email Java para Ruby es muy simple y fácil de instalar. Siga estos sencillos pasos:

1. Ejecute el siguiente comando.

``` java

 $ gem install aspose-emailjava

```

1. Descargue el componente Aspose.Email para Java requerido desde el siguiente enlace.
   <https://downloads.aspose.com/total>
1. Cree la carpeta «jars» en la raíz de la gema Java for Ruby de Aspose.Email y copie en ella el componente descargado.
## **Using**
Incluya los archivos necesarios para trabajar con **createnewemail** example.

``` java

 require File.dirname(File.dirname(File.dirname(__FILE__))) + '/lib/aspose-emailjava'

include Asposeemailjava

include Asposeemailjava::CreateNewEmail

initialize_aspose_email

```

Vamos a entender el código anterior.

1. La primera línea asegura que el correo electrónico de aspose esté cargado y disponible.
1. Incluya los archivos necesarios para acceder al correo electrónico de aspose.
1. Inicialice las bibliotecas. Las clases JAVA de aspose se cargan desde la ruta proporcionada en el archivo aspose.yml
