---
title: "Gerenciando Arquivos de Mensagem do Outlook com a API do Analisador de Email em C++"
description: "A API da Biblioteca de Análise de Email em C++ é útil para ler, escrever arquivos de modelo OFT do Outlook, gerenciar mensagens assinadas digitalmente, definir categorias de cor e acessar informações de recibo de entrega."
url: /pt/cpp/managing-message-files-with-aspose-email-outlook/
weight: 30
type: docs
linktitle: "Gerenciando Arquivos de Mensagem com Aspose.Email.Outlook"
---

## **Lendo e Escrevendo Arquivo de Modelo do Outlook (.OFT)**
Os modelos do Outlook são muito úteis quando você deseja enviar uma mensagem de email semelhante repetidamente. Em vez de preparar a mensagem do zero a cada vez, prepare primeiro a mensagem no Outlook e salve-a como um modelo do Outlook (OFT). Depois disso, sempre que precisar enviar a mensagem, você pode criá-la a partir do modelo, economizando tempo escrevendo o mesmo texto no corpo ou na linha de assunto, definindo formatação e assim por diante. A classe MailMessage da Aspose.Email pode ser usada para carregar e ler um arquivo de modelo do Outlook (OFT). Assim que o modelo do Outlook for carregado em uma instância da classe MailMessage, você poderá atualizar o remetente, destinatário, corpo, assunto e outras propriedades. Após atualizar as propriedades:

- Envie o email usando a classe SmtpClient ou
- Salve a mensagem como MSG e faça mais atualizações/validações usando o Microsoft Outlook.

Nos exemplos de código abaixo, nós:

1. Carregamos o modelo usando a classe MailMessage.
1. Atualizamos algumas das propriedades.
1. Salvamos a mensagem no formato MSG.

O seguinte trecho de código mostra como carregar o arquivo OFT com a API da Biblioteca de Análise de Email em C++, atualizando a mensagem e salvando-a no formato MSG.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadAndWritingOutlookTemplateFile-ReadAndWritingOutlookTemplateFile.cpp" >}}

## **Gerenciando Mensagens Assinadas Digitalmente**
A Aspose.Email implementa o algoritmo completo do objeto de email S/MIME. Isso dá à API o poder total de preservar assinaturas digitais ao converter mensagens entre formatos.

### **Preservando Assinatura ao Converter de EML para MSG**
Ao converter de EML para MSG, defina a flag preserveSignature como true para preservar uma assinatura. O seguinte trecho de código mostra como converter de EML para MSG.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ConvertEMLToMSG-ConvertEMLToMSG.cpp" >}}

### **Convertendo Mensagens S/MIME de MSG para EML**
A Aspose.Email preserva a assinatura digital ao converter de MSG para EML, conforme mostrado no seguinte trecho de código.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ConvertMIMEMessagesFromMSGToEML-ConvertMIMEMessagesFromMSGToEML.cpp" >}}

## **Definindo Categoria de Cor para Arquivos MSG do Outlook**
Uma categoria de cor marca uma mensagem de email para algum tipo de importância ou categoria. O Microsoft Outlook permite que os usuários atribuam categorias de cor para diferenciar emails. Para lidar com a categoria de cor, use o FollowUpManager. Ele contém funções como AddCategory, RemoveCategory, ClearCategories e GetCategories.

- AddCategory recebe MapiMessage e a string da categoria de cor, por exemplo "Categoria Roxa" ou "Categoria Vermelha" como argumentos.
- RemoveCategory recebe MapiMessage e a string da categoria de cor a ser removida da mensagem.
- ClearCategories() é usado para remover todas as categorias de cor da mensagem.
- GetCategories é usado para recuperar todas as categorias de cor de uma mensagem específica.

O seguinte exemplo realiza as tarefas descritas abaixo:

1. Adicionar uma categoria de cor.
1. Adicionar outra categoria de cor.
1. Recuperar a lista de todas as categorias.
1. Remover todas as categorias.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetColorCategories-SetColorCategories.cpp" >}}

## **Acessando Informações de Follow Up do arquivo MSG**
A API Aspose.Email fornece a capacidade de acessar as informações de follow up de uma mensagem enviada ou recebida. Ela pode recuperar as informações de Recibo de Leitura, Recibo de Entrega e resultados de votação de um arquivo de mensagem.

### **Recuperando Informações de Recibo de Leitura e Entrega**
O seguinte trecho de código mostra como recuperar informações de recibo de leitura e entrega.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-RetrieveReadAndDeliveryReceiptInformation-RetrieveReadAndDeliveryReceiptInformation.cpp" >}}