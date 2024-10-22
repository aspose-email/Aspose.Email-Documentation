---
title: "Converter ICS para Outros Formatos"
url: /pt/net/converting-between-formats/convert-ics-to-other-formats
weight: 60
type: docs
---

## **Converter ICS para EML**

Para a representação de um evento de calendário ou compromisso, o Aspose.Email possui a classe [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class). O seguinte exemplo de código demonstra o processo de conversão de ICS para EML:

1. Carregue o arquivo ICS a ser convertido usando o método [Calendar.Appointment.Load](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3).
2. Crie um novo objeto [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) para armazenar os dados do calendário. 
3. Adicione o compromisso do arquivo ICS ao EML como uma visualização alternativa usando o método [RequestApointment()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/requestapointment/#requestapointment). 
4. Salve o arquivo EML com os dados convertidos usando o método [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) com o [EmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/emlsaveoptions/emlsaveoptions/#emlsaveoptions-constructor) especificando o tipo de salvamento como EmlFormat. 

```cs
// carregar o arquivo ICS a ser convertido
var ics = Calendar.Appointment.Load("Meu Arquivo.ics");
// criar um EML
var eml = new MailMessage();
// adicionar compromisso ao EML
eml.AlternateViews.Add(ics.RequestApointment());
// salvar o EML
eml.Save("Arquivo Salvo.eml", new EmlSaveOptions(MailMessageSaveType.EmlFormat));
```

## **Converter ICS para EMLX**

Para converter um arquivo ICS para o formato EMLx, siga as instruções do artigo [Converter ICS para EML](#convert-ics-to-eml) e salve o arquivo .emlx como mostrado na seguinte linha de código:

```cs
// salvar como um EMLX
eml.Save("Arquivo Salvo.emlx", new EmlSaveOptions(MailMessageSaveType.EmlxFormat));
```

## **Converter ICS para HTML**

O seguinte exemplo de código demonstra o processo de conversão:

1. Carregue o arquivo ICS a ser convertido usando o método [Calendar.Appointment.Load](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3).
2. Crie um novo objeto [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) para armazenar os dados do calendário. 
3. Adicione o compromisso do arquivo ICS ao EML como uma visualização alternativa usando o método [RequestApointment()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/requestapointment/#requestapointment). 
4. Salve o arquivo EML com os dados convertidos usando o método [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) com o [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/#htmlsaveoptions-class) para fornecer opções de formatação para o arquivo HTML salvo. Neste caso específico, as opções [HtmlFormatOptions.WriteHeader](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/#htmlformatoptions-enumeration) são usadas para incluir o cabeçalho HTML no arquivo de saída, enquanto [HtmlFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/#htmlformatoptions-enumeration) é usado para renderizar quaisquer eventos de calendário contidos na mensagem EML em um formato adequado para exibição. 

```cs
// carregar o arquivo ICS a ser convertido
var ics = Aspose.Email.Calendar.Appointment.Load("Meu Arquivo.ics");
// criar um EML
var eml = new MailMessage();
// adicionar compromisso ao EML
eml.AlternateViews.Add(ics.RequestApointment());
// salvar EML como um HTML
eml.Save("Arquivo Salvo.html", new HtmlSaveOptions { HtmlFormatOptions = HtmlFormatOptions.WriteHeader | HtmlFormatOptions.RenderCalendarEvent });
```

Use outros valores e propriedades da enumeração [HtmlFormatOptions](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/#htmlformatoptions-enumeration) e da classe [HtmlSaveOptions](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/#htmlsaveoptions-class) para definir opções de formato conforme necessário.

## **Converter ICS para MBOX**

O seguinte exemplo de código demonstra o processo de conversão de ICS para MBOX. Ele carrega um arquivo ICS, cria uma mensagem EML, adiciona os detalhes do compromisso do arquivo ICS à mensagem EML e, em seguida, grava a mensagem EML em um arquivo de armazenamento MBOX.

1. Carregue o arquivo ICS a ser convertido usando o método [Calendar.Appointment.Load](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3).
2. Crie um novo objeto [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) para armazenar os dados do calendário. 
3. Adicione o compromisso do arquivo ICS ao EML como uma visualização alternativa usando o método [RequestApointment()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/requestapointment/#requestapointment).
4. Crie um novo objeto MboxrdStorageWriter.
5. Adicione a mensagem EML ao armazenamento escrevendo o conteúdo da mensagem no formato MBOX no arquivo MBOX especificado.

```cs
// carregar o arquivo ICS a ser convertido
var ics = Aspose.Email.Calendar.Appointment.Load("Meu Arquivo.ics");
// criar um EML
var eml = new MailMessage();
// adicionar compromisso ao EML
eml.AlternateViews.Add(ics.RequestApointment());
// criar um armazenamento MBOX
using var mboxStorage = new MboxrdStorageWriter("Arquivo Salvo.mbox" , false);
// adicionar EML ao armazenamento MBOX
mboxStorage.WriteMessage(eml);
```

## **Converter ICS para MHTML**

O seguinte exemplo de código demonstra a representação de todas essas etapas no processo de conversão usando a biblioteca Aspose.Email para .NET:

1. Carregue o arquivo ICS a ser convertido usando o método [Calendar.Appointment.Load](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3).
2. Crie um novo objeto [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/#mailmessage-class) para armazenar os dados convertidos. 
3. Adicione o compromisso do arquivo ICS ao EML como uma visualização alternativa usando o método [RequestApointment()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/requestapointment/#requestapointment).
4. Salve o arquivo EML com os dados convertidos usando o método [Save](https://reference.aspose.com/email/net/aspose.email/mailmessage/save/#save_3) com [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class) para fornecer opções de salvamento para o arquivo MHTML. Neste caso específico, as opções [MhtFormatOptions.WriteHeader](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions/#mhtformatoptions-enumeration) são usadas para incluir o cabeçalho da mensagem de email no arquivo de saída, enquanto [MhtFormatOptions.RenderCalendarEvent](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions/#mhtformatoptions-enumeration) é usado para renderizar quaisquer eventos de calendário contidos na mensagem EML em um formato adequado para exibição.

```cs
// carregar o arquivo ICS a ser convertido
var ics = Aspose.Email.Calendar.Appointment.Load("Meu Arquivo.ics");
// criar um EML
var eml = new MailMessage();
// adicionar compromisso ao EML
eml.AlternateViews.Add(ics.RequestApointment());
// salvar EML como um MHTML
eml.Save("Arquivo Salvo.mht", new MhtSaveOptions{MhtFormatOptions = MhtFormatOptions.WriteHeader | MhtFormatOptions.RenderCalendarEvent});
```

Essa abordagem garante que o arquivo MHTML convertido retenha os detalhes e a formatação do evento de calendário, permitindo o compartilhamento e a visualização eficiente em várias plataformas e clientes de email.

Sinta-se à vontade para usar outros valores e propriedades da enumeração [MhtFormatOptions](https://reference.aspose.com/email/net/aspose.email/mhtformatoptions/#mhtformatoptions-enumeration) e da classe [MhtSaveOptions](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/#mhtsaveoptions-class) para definir opções de formato conforme necessário.

## **Converter ICS para MSG**

Converter arquivos ICS (iCalendar) para o formato MSG é razoável para melhor compatibilidade com o Microsoft Outlook, uma vez que os arquivos MSG são comumente usados para armazenar mensagens de email, compromissos e outros dados relacionados ao Outlook. O seguinte exemplo de código demonstra como carregar um arquivo ICS, manipular seu conteúdo e salvá-lo como um arquivo MSG sem perder dados ou formatação:

1. Carregue o arquivo ICS usando o método [Calendar.Appointment.Load()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3) e crie um objeto [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) a partir dos dados do calendário armazenados no arquivo.
2. Chame o método [Save](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/save/#save_4) no objeto Appointment para converter e salvar os dados do compromisso carregados do arquivo ICS em um arquivo MSG no local especificado.

```cs
// carregar o arquivo ICS a ser convertido
// salvar ICS como um MSG
Aspose.Email.Calendar.Appointment.Load("Meu Arquivo.ics").Save("Arquivo Salvo.msg", AppointmentSaveFormat.Msg);
```

## **Converter ICS para OFT**

O processo envolve carregar arquivos ICS e salvá-los como arquivos MSG com conversão adicional para o formato OFT:

1. Crie um novo objeto de stream para armazenar os dados do compromisso na memória.
2. Carregue os dados do compromisso do arquivo ICS. Salve os dados do compromisso no objeto de stream no formato MSG usando o método Save().
3. Carregue os dados do compromisso do stream criando um novo objeto MapiMessage usando o método [MapiMessage.Load()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/load/#load) .
4. Salve os dados do MapiMessage carregados como um arquivo de modelo do Outlook usando o método [Save()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/save/#save_3) com as opções de formato fornecidas SaveOptions.DefaultOft.

```cs
// carregar o arquivo ICS a ser convertido
// salvar ICS como um MSG
using var msgStream = new MemoryStream();
Aspose.Email.Calendar.Appointment.Load("Meu Arquivo.ics").Save(msgStream, AppointmentSaveFormat.Msg);
// salvar MSG como um OFT
MapiMessage.Load(ms).Save("Arquivo Salvo.oft", SaveOptions.DefaultOft);
```

## **Converter ICS para OST**

O Aspose.Email fornece funcionalidade para carregar um arquivo ICS, salvá-lo como um arquivo MSG, depois abrir um arquivo OST, acessar pastas de calendário dentro do arquivo e facilmente adicionar arquivos MSG à pasta de calendário:

1. Crie um stream para armazenar os dados do compromisso.
2. Carregue os dados do compromisso de um arquivo ICS usando o método [Appointment.Load()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3) e salve-o no stream em formato MSG com o método [Appointment.Save](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/save/#save_4).
3. Carregue o arquivo de Armazenamento Pessoal usando o método [FromFile](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/fromfile/#fromfile) da classe [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class).
4. Recupere a pasta de calendário do arquivo de Armazenamento Pessoal com o método [PersoanlStorage.GetPredefinedFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/getpredefinedfolder/) .
5. Use o método [FolderInfo.AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/) para adicionar a mensagem de compromisso à pasta de calendário no arquivo OST.

```cs
// carregar o arquivo ICS a ser convertido
// salvar ICS como um MSG
using var msgStream = new MemoryStream();
Aspose.Email.Calendar.Appointment.Load("Meu Arquivo.ics").Save(msgStream, AppointmentSaveFormat.Msg);
// abrir um arquivo OST
using var pst = PersonalStorage.FromFile("Arquivo Salvo.ost");
// obter uma pasta de calendário
var calendarFolder = pst.GetPredefinedFolder(StandardIpmFolder.Appointments);
// adicionar MSG à pasta de calendário
calendarFolder.AddMessage(MapiMessage.Load(msgStream));
```

## **Converter ICS para PST**

O seguinte exemplo de código demonstra o processo de conversão:

1. Crie um stream para armazenar os dados do compromisso.
2. Carregue os dados do compromisso de um arquivo ICS usando o método [Appointment.Load()](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/load/#load_3) e salve-o no stream em formato MSG com o método [Appointment.Save](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/save/#save_4).
3. Crie um novo arquivo PST com o nome do arquivo usando o método [PersonalStorage.Create](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create_4).
4. Crie uma pasta de calendário dentro do arquivo PST para armazenar compromissos usando o método [CreatePredefinedFolder](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/createpredefinedfolder/#createpredefinedfolder).
5. Adicione a mensagem de compromisso à pasta de calendário dentro do arquivo PST usando o método [FolderInfo.AddMessage](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmessage/) .

```cs
// carregar o arquivo ICS a ser convertido
// salvar ICS como um MSG
using var msgStream = new MemoryStream();
Aspose.Email.Calendar.Appointment.Load("Meu Arquivo.ics").Save(msgStream, AppointmentSaveFormat.Msg);
// criar um arquivo PST
using var pst = PersonalStorage.Create("Arquivo Salvo.pst", FileFormatVersion.Unicode);
// criar uma pasta de calendário
var calendarFolder = pst.CreatePredefinedFolder("Calendário", StandardIpmFolder.Appointments);
// adicionar MSG à pasta de calendário
calendarFolder.AddMessage(MapiMessage.Load(msgStream));
```