---
title: "Trabalhando com Compromissos"
url: /pt/java/trabalhando-com-compromissos/
weight: 20
type: docs
---

## **Carregar e Salvar um Compromisso no formato ICS**

A [Classe Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) no Aspose.Email para Java pode ser usada para carregar um compromisso no formato ICS, bem como para criar um novo compromisso e salvá-lo em um disco no formato ICS. Neste artigo, primeiro criamos um compromisso e o salvamos em um disco no formato ICS e depois o carregamos.

### **Carregar um Compromisso no formato ICS**

Para carregar um compromisso no formato ICS, os seguintes passos são necessários:

1. Crie uma instância da [Classe Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/).
1. Chame o [método Load()](https://reference.aspose.com/email/java/com.aspose.email/appointment/#load-java.io.InputStream-) fornecendo o caminho do arquivo ICS.
1. Leia qualquer propriedade para obter qualquer informação do compromisso (arquivo ICS).

Os seguintes trechos de código mostram como carregar um compromisso no formato ICS.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-LoadAppointment.java" >}}

### **Criar um Compromisso e Salvar em Disco no formato ICS**

Os seguintes passos são necessários para criar um compromisso e salvá-lo no formato ICS.

1. Crie uma instância da [Classe Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) e inicialize-a com este construtor.
1. Passe os seguintes argumentos no construtor acima
   1. Participantes
   1. Descrição
   1. Data de Término
   1. Localização
   1. Organizador
   1. Data de Início
   1. Resumo
   1. Data de Criação
   1. Data de Última Modificação
1. Chame o [método Save()](https://reference.aspose.com/email/java/com.aspose.email/appointment/#save-java.io.OutputStream-) e especifique o nome do arquivo e o formato nos argumentos.

O compromisso pode ser aberto no Microsoft Outlook ou em qualquer programa que possa carregar um arquivo ICS. Se o arquivo for aberto no Microsoft Outlook, ele adicionará automaticamente o compromisso ao calendário do Outlook.

Os seguintes trechos de código mostram como criar e salvar um compromisso em um disco no formato ICS.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-CreateAppointment.java" >}}

## **Salvar Compromissos no formato MSG**

Aspose.Email torna possível salvar compromissos diretamente em arquivos .msg. As seguintes classes públicas estão disponíveis para personalizar o processo de salvamento de compromissos:

- [Classe AppointmentMsgSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/appointmentmsgsaveoptions/) com opções adicionais para salvar compromissos no formato msg.
- [Classe AppointmentIcsSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/appointmenticssaveoptions/) com opções adicionais para salvar compromissos no formato ics. Ela foi adicionada para substituir o IcsSaveOptions obsoleto.

O exemplo de código abaixo mostra como carregar um compromisso de um arquivo e, em seguida, salvá-lo em dois formatos diferentes: .ics e .msg.

```java
Appointment appointment = Appointment.load("fileName");
appointment.save("fileName.ics", new AppointmentIcsSaveOptions());
appointment.save("fileName.msg", new AppointmentMsgSaveOptions());
```

## **Criar um Compromisso com Conteúdo HTML**

É uma prática comum usar o cabeçalho X-ALT-DESC no formato iCalendar (RFC 5545). Trata-se de uma propriedade estendida que fornece uma descrição alternativa legível por humanos de um item ou evento de calendário. Este cabeçalho é frequentemente utilizado para incluir uma representação em texto simples ou HTML da descrição do evento, o que pode ser útil para compatibilidade com softwares de calendário mais antigos ou para fornecer uma versão simplificada da descrição. Em casos em que a descrição primária não é suportada ou exibida corretamente pelo aplicativo de calendário do destinatário, o cabeçalho X-ALT-DESC é usado para fornecer uma descrição alternativa do evento. Ele permite que o remetente inclua diferentes representações da descrição do evento para garantir melhor compatibilidade e acessibilidade entre diferentes softwares de calendário e plataformas. Para criar um compromisso com conteúdo HTML, defina a propriedade [HtmlDescription](https://reference.aspose.com/email/java/com.aspose.email/appointment/#setHtmlDescription-java.lang.String-) como 'true'. Tente o seguinte exemplo de código que demonstra como criar e definir um objeto de compromisso com detalhes e configurações específicas, incluindo a data, hora, localização, organizador, participantes e uma descrição formatada:

```java
Date startDate = new Date();
Appointment appointment = new Appointment("Bygget 83",
        startDate, // data de início
        addHours(startDate, 1), // data de término
        new MailAddress("TintinStrom@from.com", "Tintin Strom"), // organizador
        MailAddressCollection.to_MailAddressCollection(
                new MailAddress("AinaMartensson@to.com", "Aina Martensson"))); // participante
appointment.setHtmlDescription("<html>\n"
        + "     <style type=\"\"text/css\"\">\n"
        + "      .text {\n"
        + "             font-family:'Comic Sans MS';\n"
        + "             font-size:16px;\n"
        + "            }\n"
        + "     </style>\n"
        + "    <body>\n"
        + "     <p class=\"\"text\"\">Oi, estou feliz em convidá-lo para nossa festa.</p>\n"
        + "    </body>\n"
        + "    </html>");
```

## **Criar uma Solicitação de Compromisso em Rascunho**

Para salvar um compromisso no modo rascunho, a [Propriedade Method](https://reference.aspose.com/email/java/com.aspose.email/appointment/#getMethodType--) da [Classe Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/) deve ser definida como **Publicar**. O exemplo de código a seguir demonstra o uso dessa propriedade como exemplo.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-DraftAppointmentRequest-CreateADraftAppointmentRequest.java" >}}

### **Criação de Compromisso em Rascunho a partir de Texto**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-DraftAppointmentRequest-DraftAppointmentCreationFromText.java" >}}

## **Adicionar e Remover Anexos de Itens de Calendário**

Aspose.Email fornece uma coleção de anexos que pode ser usada para adicionar e recuperar anexos associados a itens de calendário. Este artigo mostra como:

1. Criar e adicionar anexos a um [Objeto Classe Appointment](https://reference.aspose.com/email/java/com.aspose.email/appointment/).
1. Recuperar informações sobre anexos de um compromisso.
1. Extrair anexos de um compromisso.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-AddAndRetrieveAttachmentFromCalendarItems-.java" >}}

## **Formatando Compromissos**

Os exemplos de programação abaixo demonstram como usar a [Classe AppointmentFormattingOptions](https://reference.aspose.com/email/java/com.aspose.email/appointmentformattingoptions/) para formatar texto e HTML.

#### **Exemplo de Programação - Formatação de Texto**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-FormattingAnAppointment-TextFormatting.java" >}}

#### **Exemplo de Programação - Formatação HTML**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-FormattingAnAppointment-HtmlFormatting.java" >}}

## **Ler Múltiplos Eventos de um Arquivo ICS**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-email-ReadMultipleEventsfromICSFile-ReadMultipleEventsfromICSFile.java" >}}

## **Escrever Múltiplos Eventos de um Arquivo ICS**

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-WriteMultipleEventsToICS.java" >}}

## **Definir o Status dos Participantes dos Convidados do Compromisso**

A API Aspose.Email para .NET permite definir o status dos convidados de compromissos ao formular uma mensagem de resposta. Isso adiciona a propriedade PARTSTAT ao arquivo ICS.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-SetParticipantStatusOfAppointmentAttendees.java" >}}

## **Personalizar o Identificador do Produto para iCalendar**

A API Aspose.Email para Java permite obter ou definir o identificador do produto que criou o objeto iCalendar.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-appointment-WorkingWithAppointments-ICSSaveOptions.cs" >}}

## **Como contornar a Validação de Endereço ao tentar Carregar Compromissos**

A API Aspose.Email para Java permite contornar o erro de validação de e-mail definindo a opção [IgnoreSmtpAddressCheck](https://reference.aspose.com/email/java/com.aspose.email/appointmentloadoptions/#getIgnoreSmtpAddressCheck--) no objeto [AppointmentLoadOptions](https://reference.aspose.com/email/java/com.aspose.email/appointmentloadoptions/#setIgnoreSmtpAddressCheck(boolean)) e passando-o na chamada de carregamento.

~~~Java
AppointmentLoadOptions lo = new AppointmentLoadOptions();
lo.setIgnoreSmtpAddressCheck(true);
Appointment appointment = Appointment.load("app.ics", lo);
~~~