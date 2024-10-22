---
title: "Cómo Ignorar Excepciones"
url: /es/java/how-to-ignore-exceptions/
weight: 290
type: docs
---


## **Soporte para Ignorar Excepciones**
La clase [ExceptionManager](https://apireference.aspose.com/email/java/com.aspose.email/ExceptionManager) proporciona la capacidad de ignorar excepciones:

### **Ejemplos de código:**

Establecer un callback para manejar excepciones:
~~~java
ExceptionManager.setIgnoreExceptionsHandler(new IgnoreExceptionsCallback() {
    //ruta de la excepción: {Módulo}\{Método}\{Acción}\{GUID}
    //ejemplo: MailMessage\Load\DecodeTnefAttachment\64149867-679e-4645-9af0-d46566cae598
    public boolean invoke(AsposeException ex, String path) {
        //Ignorar todas las excepciones en MailMessage.Load
        return path.equals("MailMessage\\Load");
    }
});
~~~

O usar una **alternativa**:
~~~java
//Ignorar todas las excepciones
ExceptionManager.setIgnoreAll(true);
~~~

Además, puedes establecer un callback para el **registro de excepciones ignoradas**:
~~~java
ExceptionManager.setIgnoreExceptionsLogHandler(new IgnoreExceptionsLogCallback() {
    public void invoke(String message) {
        System.out.println("=== EXCEPCIÓN IGNORADA === " + message);
    }
});
~~~

El usuario será notificado de que la excepción se puede ignorar mediante un mensaje de error. Por ejemplo:
~~~
Mensaje de excepción:

AsposeArgumentException: las propiedades no deben estar vacías.
Si quieres ignorar una excepción y continuar, entonces puedes usar:
ExceptionManager.getIgnoreList().add("MailMessage\\Load\\DecodeTnefAttachment\\64149867-679e-4645-9af0-d46566cae598")
El archivo adjunto TNEF no válido se interpretará como un archivo adjunto regular.
~~~