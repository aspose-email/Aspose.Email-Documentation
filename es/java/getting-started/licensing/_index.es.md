---
title: "Licenciamiento"
url: /es/java/licensing/
weight: 60
type: docs
---

{{% alert color="primary" %}} 

Puedes descargar una versión de evaluación de **Aspose.Email** para Java desde su página de descarga. La versión de evaluación proporciona absolutamente las mismas capacidades que la versión con licencia del producto. Además, la versión de evaluación simplemente se convierte en una versión licenciada cuando compras una licencia y agregas un par de líneas de código para aplicar la licencia.

Una vez que estés satisfecho con tu evaluación de **Aspose.Email**, puedes comprar una licencia en el sitio web de Aspose. Familiarízate con los diferentes tipos de suscripciones ofrecidas. Si tienes alguna pregunta, no dudes en contactar al equipo de ventas de Aspose.

Cada licencia de Aspose lleva una suscripción de un año para actualizaciones gratuitas a cualquier nueva versión o correcciones que salgan durante este tiempo. El soporte técnico es gratuito e ilimitado y se proporciona tanto a usuarios con licencia como a usuarios de evaluación.

{{% /alert %}} {{% alert color="primary" %}} 

Si deseas probar **Aspose.Email** sin las limitaciones de la versión de evaluación, solicita una licencia temporal de 30 días. Por favor consulta [¿Cómo obtener una Licencia Temporal?](https://purchase.aspose.com/temporary-license) para más información.

{{% /alert %}} 
## **Limitaciones de la Versión de Evaluación**
La versión de evaluación de Aspose.Email (sin una licencia especificada) proporciona la funcionalidad completa del producto, excepto por algunos de sus componentes como Aspose.Email.Mail, Aspose.Email.Pop3, y Aspose.Email.Imap que contienen algunas limitaciones de evaluación.

1. Se añade un archivo License.txt al archivo de mensaje guardado usando Aspose.Email
1. Solo se pueden extraer 50 correos electrónicos de una carpeta en el archivo PST
1. Solo se pueden extraer 3 archivos adjuntos así como imágenes en línea de un archivo MSG
1. El número máximo de archivos adjuntos procesados en formato CFB es 1
1. El número máximo de destinatarios procesados en formato CFB es 1
1. Añade "Mensaje de Evaluación" en el Asunto durante el guardado en formatos CFB, EML o MSG
1. La Fecha de Finalización no puede ser posterior al 31-12-2004 en el método GenerateOccurrences del patrón de recurrencia. Esto te permite probar el producto de manera significativa, pero es imposible usarlo en una aplicación de producción. Por ejemplo, puedes crear un patrón como "comenzar el 1 de enero de 2000 y repetir cada último día laborable de un mes" y generar ocurrencias para ello. Las ocurrencias después del 31 de diciembre de 2004 no se generarán en el modo de evaluación.
1. Añade "Imagen de Marca de Agua de Evaluación" durante el guardado en formatos XPS o TIFF.
1. El número máximo de direcciones de correo electrónico ambiguas y nombres para mostrar resueltos por el MS Exchange Server es 20
1. La longitud máxima del archivo de datos permitida para arrastrarse y soltarse con FileDropPanel es de 51200 bytes
1. Muestra un cuadro de mensaje con "Mensaje de Evaluación" durante una operación de arrastrar y soltar utilizada por FileDropPanel
1. Solo se extrae 1 archivo del flujo MSO dado por el método InlineAttachmentExtractor.EnumerateMsoPackage.
### **Configurando una Licencia**
La licencia es un archivo XML de texto plano que contiene detalles como el nombre del producto, el número de desarrolladores a los que está licenciada, la fecha de caducidad de la suscripción, etc. El archivo está digitalmente firmado, por lo que no modifiques el archivo; incluso la adición inadvertida de un salto de línea extra en el archivo lo invalidará.

Necesitas aplicar una licencia si deseas evitar las limitaciones de evaluación. Solo se requiere configurar una licencia una vez por aplicación o proceso.

La licencia se puede cargar desde un flujo o archivo en las siguientes ubicaciones:

1. Ruta explícita.
1. La carpeta que contiene el Aspose.Email.jar.

Usa el método License.setLicense para licenciar el componente. A menudo, la forma más fácil de establecer una licencia es poner el archivo de licencia en la misma carpeta que Aspose.Email.jar y especificar solo el nombre del archivo sin la ruta, como se muestra en el siguiente ejemplo:
#### **Configurando Licencia desde un Archivo**
En este ejemplo, **Aspose.Email** intentará encontrar el archivo de licencia en la carpeta que contiene los JARs de tu aplicación.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-licensing-ApplyLicenseFromFile-ApplyLicenseFromFile.java" >}}
#### **Configurando Licencia desde un Flujo**
Inicializa una licencia desde un flujo.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-licensing-ApplyLicenseFromFile-ApplyLicenseFromStream.java" >}}
### **Aplicar Licencia Medida**
Aspose.Email permite a los desarrolladores aplicar una clave medida. Es un nuevo mecanismo de licenciamiento. El nuevo mecanismo de licenciamiento se utilizará junto con el método de licenciamiento existente. Aquellos clientes que deseen ser facturados según el uso de las funciones de la API pueden utilizar el licenciamiento medido. Para más detalles, consulta la sección [Preguntas Frecuentes sobre Licenciamiento Medido](https://purchase.aspose.com/faqs/licensing/metered).

Se ha introducido una nueva clase Metered para aplicar la clave medida. A continuación se muestra el código de muestra que demuestra cómo establecer claves públicas y privadas medidas.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-licensing-ApplyMeteredLicense-ApplyMeteredLicense.java" >}}
## **Incluyendo el Archivo de Licencia como Integrado**
### **Validar la Licencia**
Es posible validar si la licencia se ha configurado correctamente o no. La clase [License](http://www.aspose.com/api/java/email/com.aspose.email/classes/License) tiene el campo isLicensed que devolverá verdadero si la licencia se ha configurado correctamente.

**Java**

``` cs

 License license = new License();

license.setLicense("Aspose.Email.Java.lic");

if (License.isLicensed()) {

    System.out.println("¡La Licencia está Configurada!");

}

```