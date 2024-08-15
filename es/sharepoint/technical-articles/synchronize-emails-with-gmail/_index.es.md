---
title: "Sincronizar correos electrónicos con Gmail"
url: /es/sharepoint/synchronize-emails-with-gmail/
weight: 10
type: docs
---


{{% alert color="primary" %}}

Aspose.Email para SharePoint admite los protocolos POP3 e IMAP al sincronizar correos electrónicos. Gmail también permite el acceso POP e IMAP gratuito a clientes de correo electrónico como Outlook Express, Microsoft Office Outlook, Thunderbird o cualquier API como Aspose.Network.

En este artículo se muestra cómo usar Aspose.Email para la función de sincronización de correo electrónico de SharePoint para sincronizar los correos electrónicos con Gmail.

{{% /alert %}}
## **Sincronización de correos electrónicos**
El componente de conversión de correo electrónico de Aspose.Email for SharePoint es una herramienta fácil de usar para sincronizar los correos electrónicos con la lista personalizada de correos electrónicos de SharePoint. Al ser compatible con protocolos y servidores de correo electrónico populares, como POP3, IMAP y Microsoft Exchange Server, Aspose.Email puede conectarse con una variedad de servidores de correo electrónico y sincronizar el correo electrónico.

En este artículo se explica cómo [configurar Gmail](/email/sharepoint/synchronize-emails-with-gmail/) para que los correos electrónicos se puedan descargar, [configurar SharePoint](/email/sharepoint/synchronize-emails-with-gmail/) para sincronizar correos electrónicos y cómo [ejecutar la sincronización manualmente](/email/sharepoint/synchronize-emails-with-gmail/).
### **Configuración de Gmail**
Para recibir correos electrónicos de Gmail mediante un cliente de correo electrónico, POP o IMAP deben estar habilitados en la página de configuración de Gmail. De forma predeterminada, está deshabilitada.

Para habilitar POP3 e IMAP:

1. Inicia sesión en tu cuenta de Gmail y haz clic **Settings** en la esquina superior derecha.
1. Click **Reenvío y POP/IMAP** para cambiar la configuración de POP e IMAP.
1. Habilite POP y elija la opción «Habilitar POP» adecuada:
   1. **Habilitar POP para todo el correo** para descargar todos los correos electrónicos (nuevos y antiguos).
   1. **Habilite POP para el correo que llegue de ahora en adelante** solo para descargar correos electrónicos nuevos.
1. Habilite IMAP. Para IMAP, solo hay dos opciones:
   1. **Enable** para descargar todos los mensajes de su buzón.
   1. **Disable** desactiva el servicio. No selecciones esta opción.

      **La pestaña Reenvío y POP/IMAP de Gmail**

![todo:image_alt_text](synchronize-emails-with-gmail_1.png)



### **Configuración de Aspose.Email para SharePoint**
1. En SharePoint, haga clic en **Configuración de sincronización** en el **Herramientas Aspose** cinta para abrir la ventana de configuración.
1. Especifica la configuración POP3 de Gmail para que se sincronice con Gmail mediante el protocolo POP3. Introduce la siguiente información en esta pantalla:
   1. Activar la sincronización: comprobar
   1. Protocolo: POP3
   1. Servidor de correo: pop.gmail.com
   1. Puerto: 995
   1. SSL: comprobar
   1. Dejar en el servidor: comprobar
   1. Nombre de usuario: username@gmail.com (especifique la dirección de correo electrónico completa)
   1. Contraseña: especifique la contraseña de Gmail
   1. Horario: elige «Minutamente» y «Cada 5 minutos» o lo que más te convenga
      **El cuadro de diálogo Configuración de sincronización.**

![todo:image_alt_text](synchronize-emails-with-gmail_2.png)




1. Verifique la conexión haciendo clic **Haga clic para probar los parámetros de conexión**. Si hay algún problema con las credenciales o la dirección del host, aparece un mensaje de error.
1. Click **Save** para guardar la configuración. Aspose.Email para SharePoint intenta conectarse a Gmail cada 5 minutos (o en cualquier otro momento especificado). Descarga los mensajes y actualiza la lista de correo electrónico.

Todos los archivos adjuntos, las imágenes incrustadas y el formato del cuerpo se conservan al descargar los mensajes y crear correos electrónicos en la lista personalizada de correos electrónicos de SharePoint.
### **Sincronización manual de correos electrónicos**
Para iniciar la sincronización manualmente:

1. Click **Sincronizar ahora** en el **Herramientas Aspose** cinta. Aparece el cuadro de diálogo Sincronizar ahora. La pantalla Sincronizar ahora muestra un resumen de la configuración de la cuenta de correo electrónico y el estado de la última sincronización.

   **El cuadro de diálogo Sincronizar ahora.**

![todo:image_alt_text](synchronize-emails-with-gmail_3.png)




1. Click **Sincronizar ahora**.

   **Correos electrónicos incluidos en una lista de SharePoint después de una sincronización correcta**

![todo:image_alt_text](synchronize-emails-with-gmail_4.png)




1. Haga clic en cualquier correo electrónico de la lista para abrirlo en SharePoint.

   **Un correo electrónico que se muestra en SharePoint.**

![todo:image_alt_text](synchronize-emails-with-gmail_5.png)
## **References**
- [Instalación de Aspose.Email para SharePoint](/email/sharepoint/install-aspose-email-for-sharepoint/)
- [Sincronizar correos electrónicos con el servidor de correo](/email/sharepoint/email-synchronization/)
- [Acerca del componente de sincronización de correo electrónico para SharePoint](/email/sharepoint/about-email-synchronization/)
