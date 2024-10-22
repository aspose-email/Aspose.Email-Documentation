---
title: "Licenciamiento"
url: /es/python-net/licensing/
weight: 60
type: docs
---


## **Evaluar Aspose.Email**
Puedes descargar Aspose.Email para Python a través de .NET de forma gratuita para evaluación. La versión de evaluación proporciona casi toda la funcionalidad del producto con ciertas limitaciones. La misma versión de evaluación se convierte en licenciada cuando compras una licencia y agregas un par de líneas de código para aplicar la licencia.

Si deseas probar Aspose.Email sin las limitaciones de la versión de evaluación, también puedes solicitar una Licencia Temporal de 30 Días. Por favor, consulta [¿Cómo obtener una Licencia Temporal?](https://purchase.aspose.com/temporary-license)
### **Limitaciones de la Versión de Evaluación**
La versión de evaluación de Aspose.Email (sin una licencia especificada) proporciona toda la funcionalidad del producto excepto algunas limitaciones de evaluación.

1. El archivo License.txt se agrega al archivo de mensaje guardado usando Aspose.Email
1. Solo se pueden extraer 50 correos electrónicos de una carpeta en el archivo PST
1. Solo se pueden extraer 3 archivos adjuntos y imágenes en línea de un archivo MSG
1. El número máximo de archivos adjuntos procesados en formato CFB es 1
1. El número máximo de destinatarios procesados en formato CFB es 1
1. Agrega "Mensaje de Evaluación" en el Asunto durante el guardado en formatos CFB, EML o MSG
1. La Fecha de Finalización no puede ser posterior al 31-12-2004 en el método GenerateOccurrences del patrón de recurrencia. Esto te permite probar el producto de manera significativa, pero es imposible usarlo en una aplicación de producción. Por ejemplo, puedes crear un patrón como "comenzar el 1 de enero de 2000 y repetir cada último día laborable del mes" y generar ocurrencias para ello. Las ocurrencias después del 31 de diciembre de 2004 no se generarán en modo de evaluación
1. Agrega "Imagen de Marca de Agua de Evaluación" durante el guardado en formatos XPS o TIFF.
1. El número máximo de direcciones de correo electrónico ambiguas y nombres de visualización resueltos por MS Exchange Server es 20
1. La longitud máxima del archivo de datos permitido para ser arrastrado y soltado con FileDropPanel es de 51200 bytes
1. Muestra un cuadro de mensaje con "Mensaje de Evaluación" durante una operación de arrastrar y soltar usada por FileDropPanel
1. Solo 1 archivo se extrae del flujo MSO dado por el método InlineAttachmentExtractor.EnumerateMsoPackage
## **Aplicando una Licencia**
Puedes descargar fácilmente una versión de evaluación de Aspose.Email desde su página de descargas. La versión de evaluación proporciona absolutamente las mismas capacidades que la versión licenciada de Aspose.Email. Además, la versión de evaluación simplemente se convierte en licenciada cuando compras una licencia y agregas un par de líneas de código para aplicar la licencia.
### **Acerca de la Licencia**
La licencia es un archivo XML de texto plano que contiene detalles como el nombre del producto, el número de desarrolladores a los que está licenciada, la fecha de expiración de la suscripción, etc. El archivo está digitalmente firmado, así que no modifiques el archivo. Incluso la adición inadvertida de un salto de línea extra en el archivo lo invalidará.

Debes establecer una licencia antes de utilizar Aspose.Email si quieres evitar sus limitaciones de evaluación. Solo se requiere establecer una licencia una vez por aplicación (o proceso).
### **Aplicar Licencia Usando Objeto de Archivo**
#### **Aplicar Licencia usando Objeto de Archivo**
La forma más fácil de establecer una licencia es colocar el archivo de licencia en la misma carpeta que el dll del componente (incluido en Aspose.Email) y especificar solo el nombre del archivo sin su ruta.

``` java

 // Instanciar una instancia de licencia y establecer el archivo de licencia a través de su ruta

license lic = new license();

license.set_license("Aspose.Email.Python.lic");

```

Cuando llames al método SetLicense, el nombre de licencias debe ser el mismo que el del nombre de tu archivo de licencia. Por ejemplo, puedes cambiar el nombre del archivo de licencia a "Aspose.Email.Python.lic.xml". Entonces en tu código, debes usar el nombre de licencia modificado (que es Aspose.Email.Python.lic.xml) para el método set_license.
