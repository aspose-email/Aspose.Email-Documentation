---
title: "Verificar Proteção de Senha PST"
url: /pt/java/check-pst-password-protection/
weight: 10
type: docs
---

## **Aspose.Email - Verificar Proteção de Senha PST**
O Microsoft Outlook permite que os usuários protejam arquivos PST com senha para restringir o acesso a eles. O Aspose.Email pode detectar a proteção por senha em um arquivo PST. Esta página mostra como verificar um PST em busca de uma senha e também como verificar se a senha aplicada a ele está correta.

**Java**

``` java

 if (pst.getMessageStoreProperties().contains(MapiPropertyTag.PR_PST_PASSWORD))

{

    long passwordHash = pst.getMessageStoreProperties().get_Item(MapiPropertyTag.PR_PST_PASSWORD).getLong();

    return passwordHash != 0;

}

```
## **Baixar Código em Execução**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Apache_POI-v1.0.0)
## **Baixar Código de Exemplo**
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavaapachepoi#src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/checkprotection/AsposeCheckProtection.java)
- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/blob/master/Plugins/Aspose_Email_for_Apache_POI/src/main/java/com/aspose/email/examples/asposefeatures/outlookstorage/checkprotection/AsposeCheckProtection.java)

{{% alert color="primary" %}} 

Para mais detalhes, visite [Trabalhando com Propriedades de Proteção por Senha PST](/email/java/working-with-calendar-items-in-pst-file/).

{{% /alert %}}