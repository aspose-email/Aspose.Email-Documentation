---
title: "Trabalhando com Itens de Calendário em Arquivo PST"
url: /pt/net/trabalhando-com-itens-de-calendario-em-arquivo-pst/
weight: 50
type: docs
---


## **Adicionar MapiCalendar ao PST**

[Criar um Novo Arquivo PST e Adicionar Subpastas](https://docs.aspose.com/email/pt/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolders) mostrou como criar um arquivo PST e adicionar uma subpasta a ele. Com Aspose.Email, você pode adicionar MapiCalendar à subpasta Calendar de um arquivo PST que você criou ou carregou. Abaixo estão os passos para adicionar MapiCalendar a um PST:

1. Crie um [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/) objeto.
2. Defina as propriedades do [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/) usando um construtor e métodos.
3. Crie um PST usando o método [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/).
4. Crie uma pasta predefinida (Calendar) na raiz do arquivo PST acessando a pasta raiz e, em seguida, chamando o método [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem).

O seguinte código de exemplo mostra como criar um [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/) e, em seguida, adicioná-lo à pasta de calendário de um arquivo PST recém-criado.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddMapiCalendarToPST-AddMapiCalendarToPST.cs" >}}

## **Salvar Itens de Calendário de PST no Disco em Formato ICS**

Este artigo mostra como acessar itens de calendário a partir de um arquivo PST do Outlook e salvar o calendário no disco em formato ICS. Use as classes [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) e [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/) para obter as informações do calendário. Abaixo estão os passos para salvar itens de calendário:

1. Carregue o arquivo PST na classe [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/).
1. Navegue até a pasta Calendar.
1. Obtenha o conteúdo da pasta Calendar para obter a coleção de mensagens.
1. Percorra a coleção de mensagens.
1. Chame o método [PersonalStorage.ExtractMessage()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractmessage/#extractmessage/) para obter as informações do contato na classe [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/).
1. Chame o método [MapiCalendar.Save()](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/save/#save/) para salvar o item de calendário no disco em formato ICS.

O programa abaixo carrega um arquivo PST do disco e salva todos os itens de calendário em formato ICS. Os arquivos ICS podem então ser usados em qualquer outro programa que possa carregar o arquivo padrão de calendário ICS. Aberto no Microsoft Outlook, um arquivo ICS se parece com o mostrado na captura de tela abaixo.

|![todo:image_alt_text](working-with-calendar-items-in-pst-file_1.png)|
| :- |
O seguinte código de exemplo mostra como exportar os itens de calendário do PST do Outlook para o formato ICS.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SaveCalendarItems-SaveCalendarItems.cs" >}}

### **Salvar como ICS com Timestamp Original**

Os seguintes recursos estão disponíveis para salvar itens de calendário como ICS preservando suas informações originais de data e hora:

- [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/) - Permite especificar opções adicionais ao salvar MapiCalendar no formato Ics.

- [MapiCalendarIcsSaveOptions.KeepOriginalDateTimeStamp](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/keeporiginaldatetimestamp/) - Permite manter o valor original de DateTimeStamp no arquivo de saída.

Use o exemplo de código abaixo para implementar os recursos em seu projeto:

```cs
var cal = pst.ExtractMessage(msgInfo).ToMapiMessageItem() as MapiCalendar;

if (cal != null)
{
  cal.Save("cal.ics", new MapiCalendarIcsSaveOptions() { KeepOriginalDateTimeStamp = true});
}
```

## **Modificar/Deletar Ocorrências de Recorrências**

Exceções podem ser adicionadas a recorrências existentes usando a API Aspose.Email para .NET. O seguinte exemplo de código ilustra o uso desse recurso.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ModifyDeleteOccurrenceInRecurrence-ModifyDeleteOccurrenceInRecurrence.cs" >}}