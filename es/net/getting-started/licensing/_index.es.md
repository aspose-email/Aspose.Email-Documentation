---
title: "Licenciamiento"
url: /es/net/licensing/
weight: 80
type: docs
---


## **Evaluar Aspose.Email**
Puedes descargar Aspose.Email para .NET de forma gratuita para evaluación. La versión de evaluación proporciona casi toda la funcionalidad del producto con ciertas limitaciones. La misma versión de evaluación se convierte en licenciada cuando compras una licencia y agregas un par de líneas de código para aplicar la licencia.

Si deseas probar Aspose.Email sin las limitaciones de la versión de evaluación, también puedes solicitar una Licencia Temporal de 30 Días. Por favor, consulta [¿Cómo obtener una Licencia Temporal?](https://purchase.aspose.com/temporary-license)
### **Limitaciones de la Versión de Evaluación**
La versión de evaluación de Aspose.Email (sin una licencia especificada) proporciona la funcionalidad completa del producto excepto algunas limitaciones de evaluación.

1. Se agrega el archivo License.txt al archivo de mensaje guardado utilizando Aspose.Email
1. Solo se pueden extraer 50 correos electrónicos de una carpeta en un archivo PST
1. Solo se pueden extraer 3 archivos adjuntos así como imágenes en línea de un archivo MSG
1. El número máximo de archivos adjuntos procesados en formato CFB es 1
1. El número máximo de destinatarios procesados en formato CFB es 1
1. Se añade "Mensaje de Evaluación" en el Asunto al guardar en formatos CFB, EML o MSG
1. La Fecha de Fin no puede ser posterior al 31-12-2004 en el método GenerateOccurrences del patrón de recurrencia. Esto permite probar el producto de manera significativa, pero es imposible usarlo en una aplicación de producción. Por ejemplo, puedes crear un patrón como "comenzar el 1 de enero de 2000 y repetirse cada último día laborable del mes" y generar ocurrencias para él. Las ocurrencias después del 31 de diciembre de 2004 no se generarán en modo de evaluación
1. Se añade "Imagen de Marca de Agua de Evaluación" al guardar en formatos XPS o TIFF.
1. El número máximo de direcciones de correo electrónico ambiguas y nombres para mostrar resueltos por MS Exchange Server es 20
1. La longitud máxima del archivo de datos permitida para arrastrar y soltar con FileDropPanel es de 51200 bytes
1. Muestra un cuadro de mensaje con "Mensaje de Evaluación" durante una operación de arrastrar y soltar utilizada por FileDropPanel
1. Solo 1 archivo se extrae de un flujo MSO dado por el método InlineAttachmentExtractor.EnumerateMsoPackage
## **Aplicando una Licencia**
Puedes descargar fácilmente una versión de evaluación de Aspose.Email desde su [página de descarga](https://www.nuget.org/packages/Aspose.Email/). La versión de evaluación proporciona exactamente las mismas capacidades que la versión licenciada de Aspose.Email. Además, la versión de evaluación simplemente se convierte en licenciada cuando compras una licencia y agregas un par de líneas de código para aplicar la licencia.
### **Acerca de la Licencia**
La licencia es un archivo XML de texto plano que contiene detalles como el nombre del producto, el número de desarrolladores a los que está licenciada, la fecha de caducidad de la suscripción, etc. El archivo está firmado digitalmente, así que no modifiques el archivo. Incluso la adición inadvertida de un salto de línea extra en el archivo lo invalidará.

Necesitas establecer una licencia antes de utilizar Aspose.Email si deseas evitar sus limitaciones de evaluación. Solo se requiere establecer una licencia una vez por aplicación (o proceso).
### **Aplicar Licencia Usando Objeto de Archivo o Flujo**
#### **Estableciendo una Licencia en Aspose.Email para .NET**
En Aspose.Email, la licencia puede ser cargada desde un archivo, flujo o un recurso embebido. Aspose.Email intenta encontrar la licencia en las siguientes ubicaciones:

- Ruta explícita
- La carpeta que contiene el dll del componente (incluido en Aspose.Email)
- La carpeta que contiene el ensamblado que llamó al dll del componente (incluido en Aspose.Email)
- La carpeta que contiene el ensamblado de entrada (tu .exe)
- Un recurso embebido en el ensamblado que llamó al dll del componente (incluido en Aspose.Email) Hay dos métodos comunes para establecer la licencia, que se discuten a continuación:
#### **Aplicar Licencia usando Objeto de Archivo o Flujo**
La forma más fácil de establecer una licencia es colocar el archivo de licencia en la misma carpeta que el dll del componente (incluido en Aspose.Email) y especificar solo el nombre del archivo sin su ruta.



``` java

 // Instanciar una instancia de licencia y establecer el archivo de licencia a través de su ruta

Aspose.Email.License license = new Aspose.Email.License();

license.SetLicense("Aspose.Email.lic");

```

``` java

 // Instanciar una instancia de licencia y establecer la licencia a través de un flujo

Aspose.Email.License license = new Aspose.Email.License();

license.SetLicense(myStream);

```



Cuando llames al método SetLicense, el nombre de la licencia debe ser el mismo que el del nombre de tu archivo de licencia. Por ejemplo, puedes cambiar el nombre del archivo de licencia a "Aspose.Email.lic.xml". Luego en tu código, debes usar el nombre de licencia modificado (es decir, Aspose.Email.lic.xml) para el método SetLicense.
### **Aplicar Licencia de Medición**
Aspose.Email permite a los desarrolladores aplicar una clave de medición. Es un nuevo mecanismo de licencias. El nuevo mecanismo de licencias se utilizará junto con el método de licencia existente. Aquellos clientes que deseen ser facturados en función del uso de las funciones de la API pueden utilizar la licencia medible. Para más detalles, consulta la sección [Preguntas Frecuentes sobre Licencias Medidas](https://purchase.aspose.com/faqs/licensing/metered).

Se ha introducido una nueva clase Metered para aplicar la clave de medición. A continuación se muestra un código de muestra que demuestra cómo establecer claves públicas y privadas medidas.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Licensing-ApplyMeteredLicense-ApplyMeteredLicense.cs" >}}
## **Incluir el Archivo de Licencia como un Recurso Embebido**
Otra forma conveniente de empaquetar la licencia con tu aplicación y asegurarte de que no se pierda, es incluirla como un recurso embebido en uno de los ensamblados que llama al dll del componente (incluido en Aspose.Email). Para incluir el archivo de licencia como un recurso embebido, realiza los siguientes pasos:

- En Visual Studio .NET, incluye el archivo de licencia (.lic) en el proyecto utilizando el menú Archivo | Agregar Elemento Existente...
- Selecciona el archivo en el Explorador de Soluciones y establece Acción de Compilación en Recurso Embebido en la ventana de Propiedades
- Para acceder a la licencia embebida en el ensamblado (como recurso embebido), no es necesario llamar a los métodos GetExecutingAssembly y GetManifestResourceStream de la clase System.Reflection.Assembly del Microsoft .NET Framework. Todo lo que necesitas hacer es agregar el archivo de licencia como un recurso embebido a tu proyecto y pasar el nombre del archivo de licencia al método SetLicense. La clase License encontrará automáticamente el archivo de licencia en los recursos embebidos.

Por favor revisa el ejemplo dado a continuación para entender este método de establecer la licencia (embebida) en tus aplicaciones.



``` java

 // Instanciar la clase License

Aspose.Email.License license = new Aspose.Email.License();

// Pasar solo el nombre del archivo de licencia embebido en el ensamblado

license.SetLicense("Aspose.Email.lic");

```