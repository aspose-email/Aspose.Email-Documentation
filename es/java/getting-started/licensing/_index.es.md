---
title: "Licensing"
url: /es/java/licensing/
weight: 60
type: docs
---

{{% alert color="primary" %}}

Puede descargar una versión de evaluación de **Aspose.Email** para Java desde su página de descargas. La versión de evaluación ofrece absolutamente las mismas capacidades que la versión con licencia del producto. Además, la versión de evaluación simplemente adquiere la licencia cuando se adquiere una licencia y se añaden un par de líneas de código para aplicar la licencia.

Una vez que esté satisfecho con su evaluación de **Aspose.Email**, puede comprar una licencia en el sitio web de Aspose. Familiarízate con los diferentes tipos de suscripción que se ofrecen. Si tiene alguna pregunta, no dude en ponerse en contacto con el equipo de ventas de Aspose.

Cada licencia de Aspose incluye una suscripción de un año para actualizaciones gratuitas a cualquier versión nueva o corrección que salga durante este tiempo. El soporte técnico es gratuito e ilimitado y se proporciona tanto a los usuarios con licencia como a los usuarios de evaluación.

{{% /alert %}} {{% alert color="primary" %}}

Si quieres probar **Aspose.Email** sin limitaciones de versión de evaluación, solicite una licencia temporal de 30 días. Por favor, consulte [¿Cómo obtener una licencia temporal?](https://purchase.aspose.com/temporary-license) para obtener más información.

{{% /alert %}}
## **Limitaciones de la versión de evaluación**
La versión de evaluación de Aspose.Email (sin una licencia especificada) proporciona todas las funciones del producto, excepto algunos de sus componentes, como Aspose.Email.Mail, Aspose.Email.Pop3 y Aspose.Email.Imap, que contienen algunas limitaciones de evaluación.

1. El archivo License.txt se agrega al archivo de mensajes guardado con Aspose.Email
1. Solo se pueden extraer 50 correos electrónicos de una carpeta en un archivo PST
1. Solo se pueden extraer 3 archivos adjuntos e imágenes en línea de un archivo MSG
1. El número máximo de archivos adjuntos procesados en formato CFB es 1
1. El número máximo de destinatarios procesados en formato CFB es 1
1. Añade un «mensaje de evaluación» en el asunto al guardar en formatos CFB, EML o MSG
1. La fecha de finalización no puede ser posterior al 31-12-2004 en el método GenerateOccurrencias del patrón de recurrencia. Esto le permite probar el producto de manera significativa, pero es imposible usarlo en una aplicación de producción. Por ejemplo, puede crear un patrón como «comience el 1 de enero de 2000 y repita hasta el último día hábil del mes» y generar repeticiones para él. Las ocurrencias posteriores al 31 de diciembre de 2004 no se generarán en el modo de evaluación
1. Añade la «Imagen de marca de agua de evaluación» al guardar en formatos XPS o TIFF.
1. El número máximo de direcciones de correo electrónico y nombres para mostrar ambiguos resueltos por MS Exchange Server es de 20
1. La longitud máxima del archivo de datos que se puede arrastrar y soltar con FileDropPanel es de 51200 bytes
1. Muestra el cuadro de mensaje con el «Mensaje de evaluación» durante una operación de arrastrar y soltar utilizada por FileDropPanel
1. Solo se extrae 1 archivo de una secuencia MSO determinada mediante el método InlineAttachmentExtractor.EnumerateMSOPackage
### **Configuración de una licencia**
La licencia es un archivo XML de texto plano que contiene detalles como el nombre del producto, el número de desarrolladores a los que se concede la licencia, la fecha de caducidad de la suscripción, etc. El archivo está firmado digitalmente, por lo que no lo modifique; incluso la adición inadvertida de un salto de línea adicional al archivo lo invalidará.

Debe solicitar una licencia si quiere evitar las limitaciones de la evaluación. Solo es necesario configurar una licencia una vez por aplicación o proceso.

La licencia se puede cargar desde una transmisión o un archivo en las siguientes ubicaciones:

1. Ruta explícita.
1. La carpeta que contiene el archivo Aspose.email.jar.

Utilice el método License.setLicense para licenciar el componente. A menudo, la forma más sencilla de configurar una licencia consiste en colocar el archivo de licencia en la misma carpeta que Aspose.email.jar y especificar solo el nombre del archivo sin la ruta, como se muestra en el siguiente ejemplo:
#### **Configuración de la licencia desde un archivo**
En este ejemplo **Aspose.Email** intentará encontrar el archivo de licencia en la carpeta que contiene los archivos JAR de su aplicación.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-licensing-ApplyLicenseFromFile-ApplyLicenseFromFile.java" >}}
#### **Configuración de la licencia desde Stream**
Inicializa una licencia desde una transmisión.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-licensing-ApplyLicenseFromFile-ApplyLicenseFromStream.java" >}}
### **Aplicar una licencia con contador**
Aspose.Email permite a los desarrolladores aplicar una clave medida. Es un nuevo mecanismo de concesión de licencias. El nuevo mecanismo de concesión de licencias se utilizará junto con el método de concesión de licencias existente. Los clientes que deseen que se les facture en función del uso de las funciones de la API pueden utilizar la licencia limitada. Para obtener más información, consulte [Preguntas frecuentes sobre licencias medidas](https://purchase.aspose.com/faqs/licensing/metered) section.

Se ha introducido una nueva clase Metered para aplicar la clave medida. A continuación se muestra el código de ejemplo que muestra cómo configurar claves públicas y privadas medidas.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-licensing-ApplyMeteredLicense-ApplyMeteredLicense.java" >}}
## **Incluir el archivo de licencia como un archivo embebido**
### **Validar la licencia**
Es posible validar si la licencia se ha configurado correctamente o no. El [License](http://www.aspose.com/api/java/email/com.aspose.email/classes/License) la clase tiene el campo isLicensed que devolverá el valor verdadero si la licencia se ha configurado correctamente.

**Java**

``` cs

 License license = new License();

license.setLicense("Aspose.Email.Java.lic");

if (License.isLicensed()) {

    System.out.println("License is Set!");

}

```


