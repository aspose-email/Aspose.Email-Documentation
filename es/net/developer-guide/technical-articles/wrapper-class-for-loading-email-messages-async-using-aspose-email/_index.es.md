---
title: "Clase contenedora para cargar mensajes de correo electrónico de forma asíncrona usando Aspose.Email"
url: /es/net/wrapper-class-for-loading-email-messages-async-using-aspose-email/
weight: 170
type: docs
---


## **Clase contenedora para cargar mensajes de correo electrónico**
Hay una serie de casos en los que es deseable tener la funcionalidad de tiempo de espera para abortar una acción que lleva un tiempo innecesario. En este artículo se proporciona una clase de ejemplo para utilizar la función de tiempo de espera al cargar archivos EML/MSG, lo que podría provocar retrasos muy prolongados o no cargarse. Dado que el tiempo de espera no está directamente relacionado con las operaciones de lectura/escritura del disco o la red, no sirve de mucho implementar esta función en la API que implementarla por parte del usuario escribiendo una clase contenedora en torno a Aspose.

La cancelación de un subproceso de larga ejecución se puede lograr con el uso de un delegado empaquetado que pasa el subproceso, para eliminarlo, en una variable local dentro del método que lo inició. El subproceso de larga ejecución se cancela abortándolo y el control se devuelve a la aplicación principal. El siguiente ejemplo de código proporciona un ejemplo de clase contenedora sobre la biblioteca Aspose.Email. El código también sigue un ejemplo de uso de la clase contenedora.
### **Ejemplo de programación con .NET 3.5 y versiones posteriores**


{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-WrapperMailMessage-WrapperMailMessage.cs" >}}
### **Ejemplo de programación con .NET 2.0**


{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-WrapperMailMessage_2_0-WrapperMailMessage.cs" >}}
### **Ejemplo de uso**


{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-UsingMailMessageWrapper-UsingMailMessageWrapper.cs" >}}
