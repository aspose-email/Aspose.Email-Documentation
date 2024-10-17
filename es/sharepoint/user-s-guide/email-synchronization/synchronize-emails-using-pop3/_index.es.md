---
title: "Sincronizar correos electrónicos usando POP3"
url: /es/sharepoint/synchronize-emails-using-pop3/
weight: 20
type: docs
---


{{% alert color="primary" %}} 

Este artículo muestra cómo usar la función de sincronización de correos electrónicos de Aspose.Email para sincronizar correos electrónicos con un servidor POP3. 

{{% /alert %}} 
## **Sincronizando Correos Electrónicos**
1. Haga clic en el elemento del menú “Configuración de Sincronización” en la cinta de “Herramientas de Aspose” para abrir la ventana emergente de configuración. Ingresa la siguiente información en esta pantalla: 
   1. Habilitar Sincronización: marcar
   1. Protocolo: POP3
   1. Servidor de correo: pop.host.com (la dirección de tu servidor de correo POP3)
   1. Puerto: 110 (puerto POP3)
   1. SSL: desmarcar
   1. Dejar en el Servidor: marcar
   1. Nombre de usuario: username@host.com (especificar la dirección de correo electrónico completa)
   1. Contraseña: especificar la contraseña
   1. Programar: elegir “Cada minuto” y “Cada 5 minutos” o lo que te convenga 

      **El cuadro de diálogo de Configuración de Sincronización configurado para conectarse a un servidor POP3.** 

![todo:image_alt_text](synchronize-emails-using-pop3_1.png)




1. Haga clic en **Haga clic para probar los parámetros de conexión** para verificar la conexión. Si hay algún problema con las credenciales o la dirección del host, se mostrará un mensaje de error.
1. Haga clic en **Guardar** para guardar la configuración.

{{% alert color="primary" %}} 

Para iniciar la sincronización de inmediato, haga clic en **Sincronizar Ahora** en la cinta de Herramientas de Aspose. 

{{% /alert %}}