---
title: "Visualizador de Arquivos MSG do Outlook"
url: /pt/net/outlook-msg-file-viewer/
weight: 50
type: docs
---


Este artigo trata da análise e visualização de arquivos MSG do Microsoft Outlook. Se você precisa manipular arquivos MSG em seu projeto ou aplicação, você precisa de uma API para analisar o formato MSG do Outlook. Ou, se você não tem o Microsoft Outlook instalado em seu sistema, pode construir seu próprio visualizador para obter o conteúdo do arquivo MSG.

Os exemplos de código neste artigo mostram como analisar um arquivo MSG do Outlook em uma aplicação C# usando a biblioteca Aspose.Email. Aspose.Email é uma biblioteca .NET disponível como DLL. Use esta biblioteca para visualizar arquivos MSG no Windows, web, console ou qualquer aplicação baseada em .NET. A versão de teste do Aspose.Email pode ser [baixada facilmente](http://www.aspose.com/downloads/email/net). O código-fonte do projeto abaixo está incluído nos exemplos fornecidos com o instalador.
## **Demonstração do Visualizador de MSG do Outlook**
Criamos uma simples aplicação de demonstração que pode ser usada para analisar e visualizar arquivos MSG. A interface do usuário pode ser vista abaixo: 

![todo:image_alt_text](outlook-msg-file-viewer_1.png)



O painel esquerdo mostra as unidades e pastas no sistema, assim como o explorador do Windows. Você pode navegar pelas pastas para mostrar ou filtrar os arquivos MSG. Apenas arquivos MSG aparecem no controle de lista superior na pasta correspondente na visualização em árvore. Como você pode ver pela captura de tela acima, os campos Assunto, De, Para e Cc são mostrados na lista superior. Se você clicar em qualquer MSG na lista, a mensagem correspondente é aberta e os detalhes podem ser vistos na interface abaixo do controle de lista. Usamos rótulos para exibir as informações de assunto, para, cc e de.

No painel inferior, usamos controles de guia para mostrar outros detalhes da mensagem, como o corpo do texto, corpo RTF, cabeçalho da mensagem, anexos e propriedades MAPI. Se você clicar na guia **Anexos**, ela mostra a lista de anexos no arquivo MSG (se houver). Você também pode salvar os anexos em seu sistema selecionando um anexo e clicando no botão **Salvar**. Isso abre a caixa de diálogo Salvar Arquivo. Navegue até a pasta desejada e salve o arquivo lá. A captura de tela a seguir mostra a visualização da guia **Anexos**. 

![todo:image_alt_text](outlook-msg-file-viewer_2.png)
## **Analisando e Visualizando o Conteúdo do Arquivo MSG Programaticamente**
Nesta seção, apresentaremos o código que usamos na demonstração para mostrar o conteúdo do arquivo MSG.
### **Carregando um Arquivo MSG**
A biblioteca Aspose.Email fornece a classe [MapiMessage](https://apireference.aspose.com/email/net/aspose.email.mapi/mapimessage) para carregar e analisar arquivos MSG. Você pode carregar o arquivo MSG usando uma única linha de código chamando o método estático FromFile() e passando o caminho para o arquivo MSG. O seguinte trecho de código mostra como carregar um arquivo MSG.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-LoadingMSGFile-LoadingMSGFile.cs" >}}
### **Obtendo os campos De, Para, Cc e Assunto de um Arquivo MSG**
A classe [MapiMessage](https://apireference.aspose.com/email/net/aspose.email.mapi/mapimessage) expõe propriedades e coleções para obter as informações de assunto, de, para e cc. A seguir está o código de exemplo para obter essas propriedades. O seguinte trecho de código mostra como obter os campos De, Para, Cc e Assunto de um arquivo MSG.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-GetMessageProperties-GetMessageProperties.cs" >}}
### **Obtendo os Corpos de Texto e RTF**
Podemos obter os corpos de texto e RTF da mensagem usando as propriedades da classe [MapiMessage](https://apireference.aspose.com/email/net/aspose.email.mapi/mapimessage). O seguinte trecho de código mostra como obter os corpos de texto e RTF.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-GetTheTextAndRTFBodies-GetTheTextAndRTFBodies.cs" >}}
### **Obtendo Anexos de um Arquivo MSG e Salvando no Disco**
A classe [MapiMessage](https://apireference.aspose.com/email/net/aspose.email.mapi/mapimessage) fornece a coleção [Attachments](https://apireference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/properties/attachments) para obter todos os anexos na mensagem (arquivo MSG). A propriedade MapiMessage.Attachments retorna um objeto do tipo MapiAttachmentCollection. Você pode usar um laço for-each para iterar através da coleção de anexos e listar os anexos. A classe Attachment contém o método Save() para salvar o anexo individual no disco. O seguinte trecho de código mostra como obter a lista de anexos e salvá-los.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-GetAttachmentsFromMSGFile-GetAttachmentsFromMSGFile.cs" >}}
### **Obtendo as Propriedades MAPI do Arquivo MSG**
Você pode obter as Propriedades MAPI do arquivo MSG usando a coleção Properties da classe [MapiMessage](https://apireference.aspose.com/email/net/aspose.email.mapi/mapimessage). O código de exemplo abaixo mostra como obter todas as propriedades MAPI no arquivo da mensagem.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-GetMAPIProperties-GetMAPIProperties.cs" >}}