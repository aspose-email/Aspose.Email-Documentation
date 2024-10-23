---
title: "Definir Categoria de Cor para Mensagem do Outlook"
url: /pt/java/set-color-category-for-outlook-message/
weight: 30
type: docs
---

## **Aspose.Email - Definir Categoria de Cor para Mensagem do Outlook**  
Microsoft Outlook permite que os usuários atribuam categorias de cores para diferenciar e-mails. Uma categoria de cor marca um e-mail como sendo de algum tipo de importância ou categoria. Aspose.Email fornece a mesma funcionalidade através da classe [FollowUpManager](https://apireference.aspose.com/email/java/com.aspose.email/class-use/FollowUpManager). A seguinte funcionalidade é suportada por esta classe:  

- AddCategory() recebe [MapiMessage](https://apireference.aspose.com/email/java/com.aspose.email/mapimessage) e a string da categoria de cor como argumentos.  
- removeCategory() recebe MapiMessage e a string da categoria de cor a ser removida da mensagem como argumentos.  
- clearCategories() é usado para remover todas as categorias de cor da mensagem.  
- getCategories() é usado para recuperar todas as categorias de cor de uma mensagem específica.  

**Java**  

``` java  
 MapiMessage msg = MapiMessage.fromFile(dataDir + "message.msg");  
// Adicionar categoria  
FollowUpManager.addCategory(msg, "Categoria Roxa");  
// Adicionar outra categoria  
FollowUpManager.addCategory(msg, "Categoria Vermelha");  
// Recuperar a lista de categorias disponíveis  
IList categories = FollowUpManager.getCategories(msg);  
// Remover a categoria especificada  
FollowUpManager.removeCategory(msg, "Categoria Vermelha");  
// Limpar todas as categorias  
//FollowUpManager.clearCategories(msg);  
msg.save(dataDir + "AsposeCategories.msg");  
```  
## **Baixar Código em Execução**  
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/releases/view/618811)  
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)  
## **Baixar Código de Exemplo**  
- [CodePlex](https://asposeemailjavaapachepoi.codeplex.com/SourceControl/latest#src/main/java/com/aspose/email/examples/asposefeatures/appointments/colorcategory/AsposeCategory.java)  
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/appointments/colorcategory/AsposeCategory.java)  

{{% alert color="primary" %}}  

Para mais detalhes, visite [Definindo Categoria de Cor para Arquivos de Mensagem do Outlook (MSG)](/email/java/managing-message-files-with-aspose-email-outlook/).  

{{% /alert %}}  