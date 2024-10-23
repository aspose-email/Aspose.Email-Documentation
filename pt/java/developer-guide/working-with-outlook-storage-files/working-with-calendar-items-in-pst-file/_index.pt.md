---
title: "Trabalhando com Itens de Calendário em Arquivo PST"
url: /pt/java/trabalhando-com-itens-de-calendario-em-arquivo-pst/
weight: 50
type: docs
---

## **Adicionando MapiCalendar ao PST**

[Criar Novo PST, Adicionar Subpastas e Mensagens](/email/java/create-new-pst-add-sub-folders-and-messages/) mostrou como criar um arquivo PST e adicionar uma subpasta a ele. Com Aspose.Email, você pode adicionar [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) à subpasta Calendário de um arquivo PST que você criou ou carregou.

Abaixo estão os passos para adicionar [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) a um PST:

1. Crie um objeto [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/).
1. Defina as propriedades do [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) usando um construtor e métodos.
1. Crie um PST usando o método [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.lang.String-int-).
1. Crie uma pasta predefinida (Calendário) na raiz do arquivo PST acessando a pasta raiz e, em seguida, chamando o método [addMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMapiMessageItem-com.aspose.email.IMapiMessageItem-).

O trecho de código abaixo mostra como criar um [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) e, em seguida, adicioná-lo à pasta Calendário de um arquivo PST recém-criado.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiCalendarToPST-.java" >}}

## **Salvar Itens de Calendário do Outlook PST em Disco no formato ICS**

Este artigo mostra como acessar itens de calendário de um arquivo PST do Outlook e salvar o calendário em disco no formato ICS. Ele usa as classes [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) e [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) para obter as informações do calendário.

Abaixo estão os passos para salvar os itens do calendário:

1. Carregue o arquivo PST na classe [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/).
1. Navegue até a pasta Calendário.
1. Obtenha o conteúdo da pasta Calendário para obter a coleção de mensagens.
1. Percorra a coleção de mensagens.
1. Chame o método [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) para obter as informações de contato na classe [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/).
1. Chame o método [MapiCalendar.save()](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/#save-java.io.OutputStream-) para salvar o item do calendário em disco no formato ICS.

O programa abaixo carrega um arquivo PST do disco e salva todos os itens de calendário no formato ICS. Os arquivos ICS podem ser usados em qualquer outro programa que pode carregar o arquivo de calendário ICS padrão. Se você abrir qualquer arquivo ICS no Microsoft Outlook, ele parecerá com o da captura de tela abaixo.

|![todo:image_alt_text](https://i.imgur.com/OhnGEXj.png)|
| :- |
|**Figura: Item de calendário salvo com Aspose.Email**|
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-SaveCalendarItemsFromOutlookPSTToDiskInICSFormat-.java" >}}

## **Extrair Itens de Calendário de um Arquivo PST**

A classe MapiCalendar representa um item de calendário no formato MAPI do Microsoft Outlook. Extraia uma mensagem de um arquivo PST e converta-a em um item de mensagem MAPI. O seguinte exemplo de código extrai um item de calendário de um arquivo PST e o converte em um objeto MapiCalendar para manipulação ou processamento adicional:

```java
MapiCalendar cal = (MapiCalendar) pst.extractMessage(messageInfo).toMapiMessageItem();
```
## **Salvar Itens de Calendário no formato ICS com Timestamp Original**

Use o exemplo de código acima para extrair um item de calendário de um arquivo PST e, em seguida, especifique opções adicionais para salvá-lo como ICS com timestamp original usando o método [setKeepOriginalDateTimeStamp](https://reference.aspose.com/email/java/com.aspose.email/mapicalendaricssaveoptions/#setKeepOriginalDateTimeStamp-boolean-) da classe [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mapicalendaricssaveoptions/):

```java
MapiCalendar cal = (MapiCalendar) pst.extractMessage(messageInfo).toMapiMessageItem();

if (cal != null) {
    MapiCalendarIcsSaveOptions so = new MapiCalendarIcsSaveOptions();
    so.setKeepOriginalDateTimeStamp(true);
    cal.save("cal.ics", so);
}
```
## **Modificar/Deletar Ocorrências de Recorrências**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ModifyDeleteOccurrencesFromRecurrence-ModifyDeleteOccurrencesFromRecurrence.java" >}}