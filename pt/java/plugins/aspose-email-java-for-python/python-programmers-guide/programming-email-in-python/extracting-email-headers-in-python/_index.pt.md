---
title: "Extraindo Cabeçalhos de Email em Python"
url: /pt/java/extracting-email-headers-in-python/
weight: 50
type: docs
---

## **Aspose.Email - Extraindo Cabeçalhos de Email**
Para extrair cabeçalhos de email usando **Aspose.Email Java para Python**, use o seguinte código.

**Código Python**

``` python



\# Inicializa e carrega um arquivo EML existente especificando o MessageFormat

mailMessage = self.MailMessage

message = mailMessage.load(self.dataDir + "Message.eml")

print "Imprimindo todos os cabeçalhos:"

\# Imprima todos os cabeçalhos

i=0

while (i < message.getHeaders().getCount()):

    print message.getHeaders().get(i)

    i += 1

```
## **Baixar Código em Execução**
Baixe **Extraindo Cabeçalhos de Email (Aspose.Email)** de qualquer um dos sites de codificação social mencionados abaixo:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](http://asposeemailjavapython.codeplex.com/releases/)