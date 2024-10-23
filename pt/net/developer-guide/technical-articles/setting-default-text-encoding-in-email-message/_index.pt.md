---
title: "Definindo a Codificação de Texto Padrão em Mensagens de Email"
url: /pt/net/setting-default-text-encoding-in-email-message/
weight: 120
type: docs
---


Este artigo apresenta a propriedade [MailMessage.PreferredTextEncoding](http://www.aspose.com/api/net/email/aspose.email/mailmessage/properties/preferredtextencoding) e explica como ela é utilizada. Usando esta propriedade, você pode definir a codificação de texto padrão para as seguintes propriedades:

- De: Nome para exibição
- Para: Nome para exibição
- Assunto
- Corpo
## **Definindo a Codificação de Texto Padrão**
Nas versões anteriores do Aspose.Email, a codificação de texto para as propriedades de de, para, assunto e corpo eram definidas separadamente. Para melhorar a usabilidade, adicionamos a propriedade [PreferredTextEncoding](http://www.aspose.com/api/net/email/aspose.email/mailmessage/properties/preferredtextencoding) que define todas de uma vez. Agora é mais fácil garantir que todo o texto nas propriedades acima esteja codificado corretamente na mensagem de email. O seguinte trecho de código mostra como usar uma palavra em francês como nome de exibição para endereços de email, assunto e corpo.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Email-SetDefaultTextEncoding-SetDefaultTextEncoding.cs" >}}