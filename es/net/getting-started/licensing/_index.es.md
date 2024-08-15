---
title: "Licensing"
url: /es/net/licensing/
weight: 80
type: docs
---


## **Evalúa Aspose.Email**
Puede descargar Aspose.Email para.NET de forma gratuita para su evaluación. La versión de evaluación proporciona casi todas las funciones del producto con ciertas limitaciones. La licencia de la misma versión de evaluación se adquiere cuando se adquiere una licencia y se añaden un par de líneas de código para aplicarla.

Si desea probar Aspose.Email sin limitaciones en la versión de evaluación, también puede solicitar una licencia temporal de 30 días. Consulte [¿Cómo obtener una licencia temporal?](https://purchase.aspose.com/temporary-license)
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
Puede descargar fácilmente una versión de evaluación de Aspose.Email desde su [página de descarga](https://www.nuget.org/packages/Aspose.Email/). La versión de evaluación proporciona absolutamente las mismas capacidades que la versión con licencia de Aspose.Email. Además, la versión de evaluación simplemente adquiere licencia cuando compra una licencia y agrega un par de líneas de código para aplicar la licencia.
### **Acerca de la licencia**
La licencia es un archivo XML de texto plano que contiene detalles como el nombre del producto, el número de desarrolladores a los que se concede la licencia, la fecha de caducidad de la suscripción, etc. El archivo está firmado digitalmente, así que no lo modifique. Incluso la adición inadvertida de un salto de línea adicional al archivo lo invalidará.

Debe establecer una licencia antes de utilizar Aspose.Email si desea evitar sus limitaciones de evaluación. Solo es necesario establecer una licencia una vez por aplicación (o proceso).
### **Aplicar la licencia mediante un archivo o un objeto de transmisión**
#### **Configuración de una licencia en Aspose.Email para.NET**
En Aspose.Email, la licencia se puede cargar desde un archivo, una transmisión o un recurso incrustado. Aspose.email intenta encontrar la licencia en las siguientes ubicaciones:

- Ruta explícita
- La carpeta que contiene la dll del componente (incluida en Aspose.Email)
- La carpeta que contiene el ensamblado que llamó al archivo dll del componente (incluido en Aspose.Email)
- La carpeta que contiene el ensamblado de la entrada (su.exe)
- Un recurso incrustado en el ensamblado que llamaba al archivo dll del componente (incluido en Aspose.Email) Hay dos métodos comunes para configurar la licencia, que se describen a continuación:
#### **Aplicar la licencia mediante un archivo o un objeto de transmisión**
La forma más sencilla de configurar una licencia es colocar el archivo de licencia en la misma carpeta que la del archivo dll del componente (incluido en Aspose.Email) y especificar solo el nombre del archivo sin su ruta.



``` java

 // Instantiate an instance of license and set the license file through its path

Aspose.Email.License license = new Aspose.Email.License();

license.SetLicense("Aspose.Email.lic");

```

``` java

 // Instantiate an instance of license and set the license through a stream

Aspose.Email.License license = new Aspose.Email.License();

license.SetLicense(myStream);

```



Al llamar al método setLicense, el nombre de la licencia debe ser el mismo que el del nombre del archivo de licencia. Por ejemplo, puede cambiar el nombre del archivo de licencia a «Aspose.Email.lic.xml». Luego, en su código, debe usar el nombre de licencia modificado (es decir, Aspose.Email.lic.xml) para el método setLicense.
### **Aplicar una licencia con contador**
Aspose.Email permite a los desarrolladores aplicar una clave medida. Es un nuevo mecanismo de concesión de licencias. El nuevo mecanismo de concesión de licencias se utilizará junto con el método de concesión de licencias existente. Los clientes que deseen que se les facture en función del uso de las funciones de la API pueden utilizar la licencia limitada. Para obtener más información, consulte [Preguntas frecuentes sobre licencias medidas](https://purchase.aspose.com/faqs/licensing/metered) section.

Se ha introducido una nueva clase Metered para aplicar la clave medida. A continuación se muestra el código de ejemplo que muestra cómo configurar claves públicas y privadas medidas.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Licensing-ApplyMeteredLicense-ApplyMeteredLicense.cs" >}}
## **Incluir el archivo de licencia como recurso integrado**
Otra forma interesante de empaquetar la licencia con su aplicación y asegurarse de que no se pierda es incluirla como un recurso incrustado en uno de los ensamblados que llama al archivo dll del componente (incluido en Aspose.Email). Para incluir el archivo de licencia como un recurso integrado, lleve a cabo los siguientes pasos:

- En Visual Studio .NET, incluya el archivo de licencia (.lic) en el proyecto mediante el menú Archivo | Agregar elemento existente...
- Seleccione el archivo en el Explorador de soluciones y defina Build Action como Embedded Resource en la ventana Propiedades
- Para acceder a la licencia integrada en el ensamblado (como recurso incrustado), no es necesario llamar a los métodos getExecutingAssembly y getManifestResourceStream de la clase System.Reflection.Assembly de Microsoft.NET Framework. Todo lo que tiene que hacer es agregar el archivo de licencia como un recurso incrustado a su proyecto y pasar el nombre del archivo de licencia al método SetLicense. La clase Licenseclass encontrará automáticamente el archivo de licencia en los recursos integrados.

Revise el ejemplo que se muestra a continuación para comprender este método de configuración de la licencia (integrada) en sus aplicaciones.



``` java

 // Instantiate the License class

Aspose.Email.License license = new Aspose.Email.License();

// Pass only the name of the license file embedded in the assembly

license.SetLicense("Aspose.Email.lic");

```
