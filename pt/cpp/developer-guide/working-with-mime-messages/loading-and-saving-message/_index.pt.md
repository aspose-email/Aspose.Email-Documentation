---
title: "Carregando, Salvando e Convertendo diferentes formatos de Mensagem de Email em C++"
description: "Com a Biblioteca de Análise de Email em C++, você pode carregar, salvar, exportar e converter diferentes formatos de mensagem de email, como EML, MSG, MHTML."
url: /pt/cpp/loading-and-saving-message/
weight: 30
type: docs
linktitle: "Carregando e Salvando Mensagem"
---

## **Carregando uma Mensagem com Opções de Carregamento**
O código a seguir mostra como carregar uma mensagem com opções de carregamento.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-LoadMessageWithLoadOptions-LoadMessageWithLoadOptions.cpp" >}}
## **Salvando e Convertendo Mensagens**
Aspose.Email facilita a conversão de qualquer tipo de mensagem para outro formato. Para demonstrar esse recurso, o código neste artigo carrega três tipos de mensagens do disco e as salva de volta em outros formatos. A classe base SaveOptions e as classes EmlSaveOptions, MsgSaveOptions, MhtSaveOptions, HtmlSaveOptions para configurações adicionais ao salvar MailMessage podem ser usadas para salvar mensagens em outros formatos. O artigo mostra como usar essas classes para salvar um email de exemplo como:

- Formato EML.
- Outlook MSG.
- Formato MHTML.
- Formato HTML.
### **Carregando EML e Salvando como EML**
O código a seguir mostra como carregar uma mensagem EML e salvá-la no disco no mesmo formato.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-LoadAndSaveFileAsEML-LoadAndSaveFileAsEML.cpp" >}}
### **Carregando EML e Salvando como EML Preservando as Fronteiras Originais**
O código a seguir mostra como carregar EML e salvar como EML preservando as fronteiras originais.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-PreserveOriginalBoundaries-PreservOriginalBoundaries.cpp" >}}
### **Salvando como EML Preservando Anexos TNEF**
O código a seguir mostra como salvar como EML preservando anexos TNEF.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-PreserveTNEFAttachment-PreserveTNEFAttachment.cpp" >}}
### **Carregando EML, Salvando como MSG**
O código a seguir mostra como carregar uma mensagem EML e convertê-la para MSG usando a opção apropriada do SaveOptions.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-LoadingEMLAndSavingToMSG-LoadingEMLAndSavingToMSG.cpp" >}}
### **Salvando MailMessage como MHTML**
Diferentes opções de MHTML podem ser usadas para obter os resultados desejados. O código a seguir mostra como carregar uma mensagem EML em [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage) e convertê-la para MHTML.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-SaveMailMessageAsMHTML-SaveMailMessageAsMHTML.cpp" >}}
#### **Exportando Email para MHT com TimeZone Personalizado**
A classe MailMessage fornece a propriedade TimeZoneOffset para definir um Timezone personalizado ao exportar para MHT. O código a seguir mostra como exportar um email para MHT com TimeZone personalizado.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-ExportEmailToMHTWithCustomTimezone-ExportEmailToMHTWithCustomTimezone.cpp" >}}
### **Exportando Email para EML**
O código a seguir mostra como exportar email para eml.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-ExportEmailToEML-ExportEmailToEML.cpp" >}}
