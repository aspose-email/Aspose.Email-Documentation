---
title: "Salvar Mensagem de E-mail usando Aspose.Email e Apache POI HSMF"
url: /pt/java/save-email-message-using-aspose-email-and-apache-poi-hsmf/
weight: 50
type: docs
---

## **Aspose.Email - Salvar Mensagem de E-mail**  
O método MailMessage.save está disponível para salvar mensagens de e-mail em vários formatos.  

**Java**  

```java  
 MailMessage messageMSG 	= MailMessage.load(dataDir + "message.msg");  

messageMSG.save(dataDir + "AsposeMessage.msg");  

messageMSG.save(dataDir + "AsposeMessage.eml");  

messageMSG.save(dataDir + "AsposeMessage.emlx");  

messageMSG.save(dataDir + "AsposeMessage.mht");  
```  
## **Apache POI HSMF - Salvar Mensagem de E-mail**  
O corpo do e-mail pode ser extraído para criar um novo arquivo.  

**Java**  

```java  
 String filename = "message.msg";  

MAPIMessage msg = new MAPIMessage(filename);  

PrintWriter txtOut = new PrintWriter("ApacheMessage.txt");  

txtOut.println("Corpo do E-mail: " + msg.getTextBody());  

txtOut.close();  
```  
## **Download do Código em Execução**  
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)  
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)  
## **Download do Código de Exemplo**  
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/featurescomparison/loadnsave/)  
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/featurescomparison/loadnsave)  

{{% alert color="primary" %}}  

Para mais detalhes, visite [Atualizar e Salvar um E-mail](/email/java/loading-and-saving-message/).  

{{% /alert %}}  