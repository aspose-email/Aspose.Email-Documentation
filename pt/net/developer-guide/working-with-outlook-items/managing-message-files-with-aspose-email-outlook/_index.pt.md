---
title: "Gerenciando Arquivos de Mensagens com Aspose.Email.Outlook"
url: /pt/net/managing-message-files-with-aspose-email-outlook/
weight: 30
type: docs
---

## **Obtendo um tipo de item MAPI**

O enum [MapiItemType](https://reference.aspose.com/email/net/aspose.email.mapi/mapiitemtype/) representa um tipo de item MAPI que pode ser convertido explicitamente em um objeto da classe correspondente derivada da interface [IMapiMessageItem](https://reference.aspose.com/email/net/aspose.email.mapi/imapimessageitem/#imapimessageitem-interface). Desta forma, os usuários podem evitar verificar o valor da propriedade [MessageClass](https://reference.aspose.com/email/net/aspose.email.mapi/imapimessageitem/messageclass/) antes da conversão da mensagem.

O seguinte exemplo de código mostra como definir um tipo para o item a ser convertido:

```cs
foreach (var messageInfo in folder.EnumerateMessages())
{
    var msg = pst.ExtractMessage(messageInfo);

    switch (msg.SupportedType)
    {
        // Tipo não suportado. MapiMessage não pode ser convertido para um tipo de item apropriado.
        // Use apenas no formato MSG.
        case MapiItemType.None:
            break;
        // Uma mensagem de email. A conversão não é necessária.
        case MapiItemType.Message:
            break;
        // Um item de contato. Pode ser convertido para MapiContact.
        case MapiItemType.Contact:
            var contact = (MapiContact)msg.ToMapiMessageItem();
            break;
        // Um item de calendário. Pode ser convertido para MapiCalendar.
        case MapiItemType.Calendar:
            var calendar = (MapiCalendar)msg.ToMapiMessageItem();
            break;
        // Uma lista de distribuição. Pode ser convertida em MapiDistributionList.
        case MapiItemType.DistList:
            var dl = (MapiDistributionList)msg.ToMapiMessageItem();
            break;
        // Uma entrada de diário. Pode ser convertida em MapiJournal.
        case MapiItemType.Journal:
            var journal = (MapiJournal)msg.ToMapiMessageItem();
            break;
        // Um StickyNote. Pode ser convertido para MapiNote.
        case MapiItemType.Note:
            var note = (MapiNote)msg.ToMapiMessageItem();
            break;
        // Um item de Tarefa. Pode ser convertido para MapiTask.
        case MapiItemType.Task:
            var task = (MapiTask)msg.ToMapiMessageItem();
            break;
    }
}
```
## **Salvando Email como HTML**

Aspose.Email possibilita salvar recursos de email com caminhos relativos ao exportar mensagens para o formato HTML. Este recurso fornece mais flexibilidade na forma como os recursos são vinculados no arquivo HTML de saída, facilitando o compartilhamento e a exibição de emails salvos em diferentes sistemas. Para salvar recursos com caminhos relativos, utilize a propriedade [HtmlSaveOptions.UseRelativePathToResources](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/userelativepathtoresources/). O valor padrão da propriedade é false (recursos são salvos com caminhos absolutos). Quando definido como true, os recursos são salvos com caminhos relativos.

Os arquivos HTML com caminhos relativos são mais portáteis e podem ser visualizados corretamente, independentemente da estrutura de arquivos do ambiente de hospedagem. Você pode escolher entre caminhos absolutos e relativos, dependendo das necessidades. Você pode definir caminhos personalizados para recursos usando o evento [ResourceHtmlRendering](https://reference.aspose.com/email/net/aspose.email/resourcehtmlrenderingeventargs/).

O seguinte exemplo de código demonstra como **salvar um email com o caminho relativo padrão para recursos**:

```cs
var msg = MapiMessage.Load(sourceFileName);

var htmlSaveOptions = new HtmlSaveOptions
{
    ResourceRenderingMode = ResourceRenderingMode.SaveToFile,
    UseRelativePathToResources = true
};

msg.Save(Path.Combine("target_files"), htmlSaveOptions);
```
Nesse caso, os recursos serão salvos na pasta [html file name]_files, no mesmo caminho que o arquivo .html e o HTML fará referência aos recursos via caminhos relativos.

O exemplo de código abaixo demonstra como **salvar com caminho absoluto para recursos**:

```cs
var msg = MapiMessage.Load(sourceFileName);

var htmlSaveOptions = new HtmlSaveOptions
{
    ResourceRenderingMode = ResourceRenderingMode.SaveToFile,
    UseRelativePathToResources = false
};

msg.Save(Path.Combine("target_files"), htmlSaveOptions);
```
Como no primeiro caso, os recursos serão salvos na pasta [html file name]_files por padrão, mas o HTML fará referência aos recursos usando caminhos absolutos.

Usando o evento [ResourceHtmlRendering](https://reference.aspose.com/email/net/aspose.email/resourcehtmlrenderingeventargs/), você pode definir caminhos personalizados relativos ou absolutos para recursos. Ao personalizar caminhos com o manipulador de eventos [ResourceHtmlRendering](https://reference.aspose.com/email/net/aspose.email/resourcehtmlrenderingeventargs/), e já que [UseRelativePathToResources](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/userelativepathtoresources/) está definido como true, você deve atribuir um caminho relativo à propriedade [PathToResourceFile](https://reference.aspose.com/email/net/aspose.email/resourcehtmlrenderingeventargs/pathtoresourcefile/) para garantir a referência correta.

O seguinte exemplo de código demonstra como **caminho relativo personalizado usando o Evento ResourceHtmlRendering**:

```cs
var msg = MapiMessage.Load(sourceFileName);

var htmlSaveOptions = new HtmlSaveOptions
{
    ResourceRenderingMode = ResourceRenderingMode.SaveToFile,
    UseRelativePathToResources = true
};

htmlSaveOptions.ResourceHtmlRendering += (o, args) =>
{
    if (o is AttachmentBase attachment)
    {
	    // Como UseRelativePathToResources = true, você deve atribuir um caminho relativo à propriedade PathToResourceFile.
        args.PathToResourceFile = $@"images\{attachment.ContentType.Name}";
    }
};

msg.Save(Path.Combine(targetPath, "A Day in the Park.html"), htmlSaveOptions);
```

## **Convertendo MSG para mensagem MIME**

A API Aspose.Email fornece a capacidade de converter arquivos MSG em mensagens MIME usando o método [ToMailMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/tomailmessage/#tomailmessage).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ConvertMSGToMIMEMessage-ConvertMSGToMIMEMessage.cs" >}}

## **Definindo Tempo Limite para Conversão de Mensagens e Processo de Carregamento**

Os seguintes recursos permitirão que você defina o tempo limite em milissegundos para o processo de conversão e carregamento:

- Propriedade [MailConversionOptions.Timeout](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/timeout/#mailconversionoptionstimeout-property) - Limita o tempo em milissegundos ao converter uma mensagem.
  
- [MailConversionOptions.TimeoutReached](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/timeoutreached/) - Levantada se o tempo esgotar ao converter para MailMessage.

- Propriedade [MsgLoadOptions.Timeout](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/timeout/) - Limita o tempo em milissegundos ao converter uma mensagem.

- [MsgLoadOptions.TimeoutReached](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/timeoutreached/) - Levantada se o tempo esgotar ao converter para MailMessage.

O exemplo de código abaixo mostrará como definir um tempo limite enquanto converte uma mensagem:

```cs
var options = new MailConversionOptions();
// Defina o tempo limite para 5 segundos
options.Timeout = 5000;

options.TimeoutReached += (object sender, EventArgs args) =>
{
    string subj = (sender as MailMessage).Subject;
	 // Defina um sinalizador indicando que o tempo limite foi atingido
    isTimedOut = true;
};

var mailMessage = mapiMessage.ToMailMessage(options);
```

## **Lendo e Gravando Arquivo de Modelo do Outlook (.OFT)**

Os modelos do Outlook são muito úteis quando você deseja enviar uma mensagem de email similar repetidamente. Em vez de preparar a mensagem do zero a cada vez, primeiro, prepare a mensagem no Outlook e salve-a como um Modelo do Outlook (OFT). Depois disso, sempre que você precisar enviar a mensagem, pode criá-la a partir do modelo, economizando tempo escrevendo o mesmo texto no corpo ou na linha de assunto, definindo formatação e assim por diante. A classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) do Aspose.Email pode ser usada para carregar e ler um arquivo de modelo do Outlook (OFT). Uma vez que o modelo do Outlook esteja carregado em uma instância da classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/), você pode atualizar o remetente, destinatário, corpo, assunto e outras propriedades. Após atualizar as propriedades:

- Envie o email usando a classe [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) ou
- Salve a mensagem como MSG e faça mais atualizações/validações usando o Microsoft Outlook.

Nos exemplos de código abaixo, nós:

1. Carregamos o modelo usando a classe [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/).
1. Atualizamos algumas das propriedades.
1. Salvamos a mensagem no formato MSG.

O seguinte trecho de código mostra como carregar o arquivo OFT, atualizar a mensagem e salvá-la no formato MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadAndWritingOutlookTemplateFile-ReadAndWritingOutlookTemplateFile.cs" >}}

### **Salvando arquivo MSG do Outlook como Modelo**

O seguinte trecho de código mostra como salvar o arquivo MSG do outlook como um modelo.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SaveMsgAsTemplate-SaveMsgAsTemplate.cs" >}}

### **Determinar se um MapiMessage é OFT ou MSG**

Ao carregar um objeto MapiMessage a partir de um arquivo, você pode precisar determinar se a mensagem carregada é um arquivo de modelo ou um arquivo de email regular. Usando a propriedade [IsTemplate](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/istemplate/) da classe [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/#mapimessage-class), você pode detectar com precisão se um email é um modelo ou não. Esta funcionalidade pode ser valiosa ao lidar e processar vários tipos de arquivos de email dentro de aplicativos e sistemas.

O exemplo de código abaixo demonstra como determinar se um MapiMessage é OFT ou MSG:

```cs
var msg = MapiMessage.Load("message.msg");
var isOft = msg.IsTemplate; // retorna false

var msg = MapiMessage.Load("message.oft");
var isOft = msg.IsTemplate; // retorna true
```

### **Salvando MapiMessage ou MailMessage no formato OFT**

A classe [SaveOptions](https://reference.aspose.com/email/net/aspose.email/saveoptions/#saveoptions-class) permite que você especifique opções adicionais ao salvar um MailMessage ou MapiMessage em um formato particular.

O seguinte exemplo de código demonstra como salvar uma mensagem no formato OFT:

```cs
// Salve o MailMessage no formato OFT
using (var eml = MailMessage.Load("message.eml"))
{
    eml.Save("message.oft", SaveOptions.DefaultOft);
	
	// ou alternativa #2
	var saveOptions = new MsgSaveOptions(MailMessageSaveType.OutlookTemplateFormat);
    eml.Save("message.oft", saveOptions);
	
	// ou alternativa  forma #3
	saveOptions = SaveOptions.CreateSaveOptions(MailMessageSaveType.OutlookTemplateFormat);
    eml.Save("message.oft", saveOptions);

}

// Salve o MapiMessage no formato OFT
using (var msg = MapiMessage.Load("message.msg"))
{
    msg.Save("message.oft", SaveOptions.DefaultOft);
	
	// ou alternativa #2
	var saveOptions = new MsgSaveOptions(MailMessageSaveType.OutlookTemplateFormat);
    msg.Save("message.oft", saveOptions);
	
	// ou alternativa  forma #3
	saveOptions = SaveOptions.CreateSaveOptions(MailMessageSaveType.OutlookTemplateFormat);
    msg.Save("message.oft", saveOptions);
}
```

## **Gerenciando Mensagens Digitalmente Assinadas**

Aspose.Email implementa o algoritmo completo do objeto de email S/MIME. Isso dá à API todo o poder para preservar assinaturas digitais ao converter mensagens entre formatos.

### **Preservando a Assinatura ao Converter de EML para MSG**

Aspose.Email preserva a assinatura digital ao converter de EML para MSG. O seguinte trecho de código mostra como converter de EML para MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ConvertEMLToMSG-ConvertEMLToMSG.cs" >}}

### **Convertendo Mensagens S/MIME de MSG para EML**

Aspose.Email preserva a assinatura digital ao converter de MSG para EML, como mostrado no seguinte trecho de código.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ConvertMIMEMessagesFromMSGToEML-ConvertMIMEMessagesFromMSGToEML.cs" >}}

### **Verificando a Assinatura de Emails Seguros**

Os seguintes recursos estão disponíveis para verificar a assinatura de objetos MapiMessage.

- Classe [SecureEmailManager](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/#secureemailmanager-class) para verificar a assinatura de emails seguros.
- Classe [SmimeResult](https://reference.aspose.com/email/net/aspose.email/smimeresult/#smimeresult-class) para armazenar os resultados da verificação.
- Método [SecureEmailManager.CheckSignature(MapiMessage msg)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_3).
- Método [SecureEmailManager.CheckSignature(MapiMessage msg, X509Certificate2 certificateForDecrypt)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_4).
- Método [SecureEmailManager.CheckSignature(MapiMessage msg, X509Certificate2 certificateForDecrypt, X509Store store)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_5).

O exemplo de código abaixo mostra como implementar os recursos em seu projeto:

```cs
var msg = MapiMessage.Load(fileName, new EmlLoadOptions());
var result = new SecureEmailManager().CheckSignature(msg);

var certFileName = "cert.pfx";
var cert = new X509Certificate2(certFileName, "pass");
var eml = MapiMessage.Load(fileName);
var store = new X509Store();
store.Open(OpenFlags.ReadWrite);
store.Add(cert);
store.Close();

var result = new SecureEmailManager().CheckSignature(eml, cert, store);
```

### **Removendo uma Assinatura de um MapiMessage**

Para melhor compatibilidade, o método [MapiMessage.RemoveSignature](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/removesignature/) e a propriedade [MapiMessage.IsSigned](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/issigned/) são usados para remover uma assinatura digital de uma mensagem.

O seguinte trecho de código mostra como implementar esses recursos em seu projeto:

```cs
var msg = MapiMessage.Load(fileName);

if (msg.IsSigned)
{
    var unsignedMsg = msg.RemoveSignature();
}
```
## **Descriptografar um MapiMessage com Certificado**

Se você tiver mensagens MAPI criptografadas e precisar descriptografá-las usando a chave privada armazenada em um certificado, os seguintes recursos do Aspose.Email podem ser úteis:

- [MapiMessage.IsEncrypted](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/isencrypted/#mapimessageisencrypted-property) - Obtém um valor que indica se a mensagem está criptografada.
- [MapiMessage.Decrypt()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/decrypt/#decrypt) - Descriptografa esta mensagem (o método pesquisa as lojas do usuário e do computador atuais para o certificado e chave privada apropriados).
- [MapiMessage.Decrypt(X509Certificate2 certificate)](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/decrypt/#decrypt_1) - Descriptografa esta mensagem com o certificado.

O seguinte exemplo de código mostra como trabalhar com mensagens MAPI criptografadas:

```cs
var privateCert = new X509Certificate2(privateCertFile, "password");
var msg = MapiMessage.Load("encrypted.msg");

if (msg.IsEncrypted);
{
    var decryptedMsg = msg.Decrypt(privateCert);
}
```

## **Definindo Categoria de Cor para Arquivos MSG do Outlook**

Uma categoria de cor marca uma mensagem de email para algum tipo de importância ou categoria. O Microsoft Outlook permite que os usuários atribuam categorias de cor para diferenciar emails. Para manipular a categoria de cor, use o [FollowUpManager](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/). Ele contém funções como [AddCategory](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/addcategory/#addcategory), [RemoveCategory](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/removecategory/#removecategory), [ClearCategories](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/clearcategories/#clearcategories) e [GetCategories](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/getcategories/#getcategories).

- [AddCategory](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/addcategory/#addcategory) aceita [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) e a string da categoria de cor, por exemplo, "Categoria Roxa" ou "Categoria Vermelha" como argumentos.
- [RemoveCategory](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/removecategory/#removecategory) aceita [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) e a string da categoria de cor a ser removida da mensagem.
- [ClearCategories](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/clearcategories/#clearcategories) é usado para remover todas as categorias de cor da mensagem.
- [GetCategories](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/getcategories/#getcategories) é usado para recuperar todas as categorias de cor de uma mensagem em particular.

O seguinte exemplo realiza as tarefas conforme descrito abaixo:

1. Adicione uma categoria de cor.
1. Adicione outra categoria de cor.
1. Recupere a lista de todas as categorias.
1. Remova todas as categorias.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetColorCategories-SetColorCategories.cs" >}}

## **Acessando Informações de Acompanhamento do arquivo MSG**

A API Aspose.Email fornece a capacidade de acessar as informações de acompanhamento de uma mensagem enviada ou recebida. Ela pode recuperar as informações de Read, Delivery Read Receipt e resultados de voto de um arquivo de mensagem.

### **Recuperando Informações de Recibo de Leitura e Entrega**

O seguinte trecho de código mostra como recuperar informações de recibo de leitura e entrega.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-RetrieveReadAndDeliveryReceiptInformation-RetrieveReadAndDeliveryReceiptInformation.cs" >}}

## **Criando Mensagens de Encaminhamento e Resposta**

A API Aspose.Email fornece a capacidade de criar e formatar as mensagens de encaminhamento e resposta. As classes [ReplyMessageBuilder](https://reference.aspose.com/email/net/aspose.email.tools/replymessagebuilder/) e [ForwardMessageBuilder](https://reference.aspose.com/email/net/aspose.email.tools/forwardmessagebuilder/) da API são usadas para criar, respectivamente, as mensagens de Resposta e Encaminhamento. Uma mensagem de Resposta ou Encaminhamento pode ser especificada para ser criada usando qualquer um dos modos do enum [OriginalMessageAdditionMode](https://reference.aspose.com/email/net/aspose.email.tools/originalmessageadditionmode/). Este enum possui os seguintes valores:

- **OriginalMessageAdditionMode.None** - A mensagem original não está incluída na mensagem de resposta.
- **OriginalMessageAdditionMode.Attachment** - A mensagem original é incluída como um anexo na mensagem de resposta.
- **OriginalMessageAdditionMode.Textpart** - A mensagem original é incluída como um texto no corpo da mensagem de resposta.

### **Criando uma Mensagem de Resposta**

O seguinte trecho de código mostra como criar uma mensagem de resposta.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreatReplyMessage-CreatReplyMessage.cs" >}}

### **Criando uma Mensagem de Encaminhamento**

O seguinte trecho de código mostra como criar uma mensagem de encaminhamento.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateForwardMessage-CreatForwardMessage.cs" >}}