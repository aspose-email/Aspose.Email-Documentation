---
title: "Crear nuevo PST en Ruby"
url: /es/java/crear-nuevo-pst-en-ruby/
weight: 70
type: docs
---

## **Aspose.Email - Crear nuevo PST**
Para crear un nuevo PST utilizando **Aspose.Email Java para Ruby**, simplemente invoque el módulo **CreatePST**. Aquí puede ver un ejemplo de código.

**Código Ruby**

``` ruby

 data_dir = File.dirname(File.dirname(File.dirname(File.dirname(__FILE__)))) + '/data/'

\# Crear una instancia de PersonalStorage

pst = Rjb::import('com.aspose.email.PersonalStorage').create(data_dir + "sample1.pst", 0)

\# Crear una carpeta en la raíz del pst

pst.getRootFolder().addSubFolder("myInbox")

\# Agregar mensaje a la carpeta recién creada

mapi_message = Rjb::import('com.aspose.email.MapiMessage')

pst.getRootFolder().getSubFolder("myInbox").addMessage(mapi_message.fromFile(data_dir + "Message.msg"))

puts "PST creado exitosamente."

```
## **Descargar código en ejecución**
Descargue **Crear nuevo PST (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_Java_for_Ruby/lib/asposeemailjava/Outlook/createpst.rb)