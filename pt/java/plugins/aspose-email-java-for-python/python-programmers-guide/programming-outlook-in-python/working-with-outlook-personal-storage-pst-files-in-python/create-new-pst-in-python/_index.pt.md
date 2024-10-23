---
title: "Criar Novo PST em Python"
url: /pt/java/create-new-pst-in-python/
weight: 50
type: docs
---

## **Aspose.Email - Criar Novo PST**
Para Criar Novo PST usando **Aspose.Email Java para Python**, use o código a seguir.

**Código em Python**

``` python



\# Criar uma instância de PersonalStorage

personalStorage = self.PersonalStorage

pst = personalStorage.create(self.dataDir + "sample1.pst", 0)

\# Criar uma pasta na raiz do pst

pst.getRootFolder().addSubFolder("myInbox")

\# Adicionar mensagem à pasta recém-criada

mapi_message = self.MapiMessage

pst.getRootFolder().getSubFolder("myInbox").addMessage(mapi_message.fromFile(self.dataDir + "Message.msg"))

print "PST criado com sucesso."

```
## **Baixar Código em Execução**
Baixe **Criar Novo PST (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavapython)