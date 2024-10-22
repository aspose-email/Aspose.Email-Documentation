---
title: "Clase Wrapper para cargar mensajes de correo electrónico de forma asíncrona usando Aspose.Email"
url: /es/net/clase-wrapper-para-cargar-mensajes-de-correo-electronico-de-forma-asinc-using-aspose-email/
weight: 170
type: docs
---


## **Clase Wrapper para cargar mensajes de correo electrónico**
Hay varias ocasiones en las que es deseable tener funcionalidad de tiempo de espera para abortar una acción que está consumiendo un tiempo innecesario. Este artículo proporciona una clase de ejemplo para lograr la funcionalidad de tiempo de espera mientras se cargan archivos EML/MSG que podrían llevar a demoras muy largas o fallar al cargar. Dado que el tiempo de espera no está relacionado directamente con la operación de lectura/escritura en disco o red, es poco útil implementar esta característica dentro de la API que tenerla implementada en el lado del usuario escribiendo una clase wrapper alrededor de Aspose.

Cancelar un hilo que se está ejecutando por mucho tiempo se puede lograr con el uso de un delegado envuelto que pasa el hilo, que debe ser terminado, en una variable local dentro del método que lo inició. El hilo de larga ejecución se cancela abortándolo y el control se devuelve a la aplicación principal. El siguiente ejemplo de código proporciona una clase wrapper de ejemplo alrededor de la biblioteca Aspose.Email. El código también sigue un ejemplo de uso de la clase wrapper.
### **Ejemplo de programación con .NET 3.5 y superior**


{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-WrapperMailMessage-WrapperMailMessage.cs" >}}
### **Ejemplo de programación con .NET 2.0**


{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-WrapperMailMessage_2_0-WrapperMailMessage.cs" >}}
### **Ejemplo de uso**


{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-UsingMailMessageWrapper-UsingMailMessageWrapper.cs" >}}