---
title: "Licensing"
url: /es/python-net/licensing/
weight: 60
type: docs
---


## **Evalúa Aspose.Email**
Puede descargar Aspose.Email para Python a través de.NET de forma gratuita para su evaluación. La versión de evaluación proporciona casi todas las funciones del producto con ciertas limitaciones. La licencia de la misma versión de evaluación se adquiere cuando se adquiere una licencia y se añaden un par de líneas de código para aplicarla.

Si desea probar Aspose.Email sin limitaciones en la versión de evaluación, también puede solicitar una licencia temporal de 30 días. Consulte [¿Cómo obtener una licencia temporal?](https://purchase.aspose.com/temporary-license)
### **Limitaciones de la versión de evaluación**
La versión de evaluación de Aspose.Email (sin una licencia especificada) proporciona la funcionalidad completa del producto, excepto algunas limitaciones de evaluación.

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
## **Solicitud de una licencia**
Puede descargar fácilmente una versión de evaluación de Aspose.Email desde su página de descargas. La versión de evaluación ofrece absolutamente las mismas capacidades que la versión con licencia de Aspose.Email. Además, la versión de evaluación simplemente adquiere licencia cuando compra una licencia y agrega un par de líneas de código para aplicar la licencia.
### **Acerca de la licencia**
La licencia es un archivo XML de texto plano que contiene detalles como el nombre del producto, el número de desarrolladores a los que se concede la licencia, la fecha de caducidad de la suscripción, etc. El archivo está firmado digitalmente, así que no lo modifique. Incluso la adición inadvertida de un salto de línea adicional al archivo lo invalidará.

Debe establecer una licencia antes de utilizar Aspose.Email si desea evitar sus limitaciones de evaluación. Solo es necesario establecer una licencia una vez por aplicación (o proceso).
### **Aplicar la licencia mediante un objeto de archivo**
#### **Aplicar la licencia mediante el objeto de archivo**
La forma más sencilla de configurar una licencia es colocar el archivo de licencia en la misma carpeta que la del archivo dll del componente (incluido en Aspose.Email) y especificar solo el nombre del archivo sin su ruta.

``` java

 // Instantiate an instance of license and set the license file through its path

license lic = new license();

license.set_license("Aspose.Email.Python.lic");

```

Al llamar al método setLicense, el nombre de la licencia debe ser el mismo que el del nombre del archivo de licencia. Por ejemplo, puede cambiar el nombre del archivo de licencia a «Aspose.Email.python.lic.xml». Luego, en su código, debe usar el nombre de licencia modificado (es decir, Aspose.Email.python.lic.xml) para el método set_license.
