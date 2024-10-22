---
title: "Recursos de Utilidade - MailMessage"
description: "Você pode ler mensagens de email com anexos TNEF usados pelo Microsoft Outlook e Exchange Server, e modificar o conteúdo do anexo usando a API da Biblioteca de Análise de Email em C++."
url: /pt/cpp/utility-features-mailmessage/
weight: 40
type: docs
---

## **MailMessages Contendo anexos TNEF**
O Formato de Encapsulamento Neutro de Transporte (TNEF) é um formato proprietário de anexo de email usado pelo Microsoft Outlook e Microsoft Exchange Server. A API Aspose.Email permite que você leia mensagens de email que possuem anexos TNEF e modifique o conteúdo do anexo. O email pode então ser salvo como um email normal ou no mesmo formato, preservando os anexos TNEF. Este artigo mostra diferentes exemplos de código para trabalhar com mensagens contendo anexos TNEF. Este artigo também mostra como criar arquivos TNEF EML a partir de arquivos MSG do Outlook.

### **Lendo Mensagem Preservando Anexos TNEF**
O seguinte trecho de código mostra como ler mensagens preservando anexos TNEF.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-ReadMessageByPreservingTNEFAttachments-ReadMessageByPreservingTNEFAttachments.cpp" >}}

## **Verificando Mensagens Devolvidas**
É muito comum que uma mensagem enviada a um destinatário possa ser devolvida por qualquer motivo, como endereço de destinatário inválido. A API Aspose.Email tem a capacidade de processar tal mensagem para verificar se é um email devolvido ou uma mensagem de email normal. O método CheckBounced da MailMessage retorna um resultado válido se a mensagem de email for um email devolvido. Este artigo mostra o uso da classe BounceResult que fornece a capacidade de verificar se uma mensagem é um email devolvido. Ele fornece informações detalhadas sobre os destinatários, a ação tomada e o motivo da notificação. O seguinte trecho de código mostra como processar mensagens devolvidas.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Email-CheckBouncedMessage-CheckBouncedMessage.cpp" >}}