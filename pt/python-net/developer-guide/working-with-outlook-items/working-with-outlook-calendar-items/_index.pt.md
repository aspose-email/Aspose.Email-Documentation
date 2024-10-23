---
title: "Trabalhando com Itens do Calendário do Outlook"
url: /pt/python-net/trabalhando-com-itens-do-calendario-do-outlook/
weight: 80
type: docs
---


## **Trabalhando com MapiCalendar**
A classe MapiCalendar da Aspose.Email fornece métodos e atributos para definir várias propriedades de um item de calendário.

### **Criando e Salvando Itens de Calendário**
O seguinte trecho de código mostra como criar e salvar um item de calendário no formato ICS.

```cs
import aspose.email as ae
from datetime import datetime

data_dir = "caminho/para/diretorio/de/dados"

# Criar a reunião
calendar = ae.mapi.MapiCalendar(
    "LAKE ARGYLE WA 6743",
    "Reunião",
    "Esta é uma reunião muito importante :)",
    datetime(2012, 4, 1),
    datetime(2012, 5, 1))

calendar.save(data_dir + "CalendarItem_out.ics", ae.calendar.AppointmentSaveFormat.ICS)
```
### **Salvando o Item de Calendário como MSG**
O seguinte trecho de código mostra como salvar o item de calendário como MSG.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-CreateAndSaveCalendarItems-CreateAndSaveCalendarItems.py" >}}

### **Definindo um ID de Produto ao Salvar MapiCalendar em ICS**

A biblioteca Aspose.Email permite que você salve um MapiCalendar (um item de calendário) em um arquivo ICS (iCalendar) com opções específicas. Com as propriedades *ics_save_options.keep_original_date_time_stamp* e *ics_save_options.product_identifier* você pode reter os carimbos de data e hora originais associados ao item de calendário e definir o identificador do produto no arquivo ICS, por exemplo, como "Foo Ltd", respectivamente. O identificador do produto é um campo que identifica o software ou serviço que gerou o arquivo ICS.

Aqui está um exemplo de código que permite definir um ID de produto ao salvar MapiCalendar em ICS:

```python
import aspose.email as ae

ics_save_options = ae.mapi.MapiCalendarIcsSaveOptions()
ics_save_options.keep_original_date_time_stamp = True
ics_save_options.product_identifier = "Foo Ltd"

mapiCalendar.save("my.ics", ics_save_options)
```
### **Obtendo o número total de eventos**

A funcionalidade da classe [CalendarReader](https://reference.aspose.com/email/python-net/aspose.email.calendar/calendarreader/) permite que você leia dados de calendário de um arquivo especificado. Ao criar um objeto CalendarReader, podemos extrair informações importantes, como o número total de eventos, a versão do calendário, o método usado e se o calendário contém múltiplos eventos. O seguinte trecho de código demonstra como trabalhar com dados de calendário e, adicionalmente, carregar os compromissos do calendário como uma lista de múltiplos eventos.

```python
import aspose.email as ae

reader = ae.calendar.CalendarReader(fileName)
print(f"O calendário contém {reader.count} eventos")
print(f"A versão do calendário é {reader.version}")
print(f"O método do calendário é {reader.method}")
print(f"O calendário contém múltiplos eventos? - {reader.is_multi_events}")
appointments = reader.load_as_multiple()
```

### **Adicionando lembrete de exibição a um Calendário**
O seguinte trecho de código mostra como adicionar um lembrete de exibição a um calendário.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddDisplayReminderToCalendar-AddDisplayReminderToCalendar.py" >}}
### **Adicionando lembrete de áudio a um Calendário**
O seguinte trecho de código mostra como adicionar um lembrete de áudio a um calendário.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddAudioReminderToCalendar-AddAudioReminderToCalendar.py" >}}

### **Adicionar/Recuperar anexos de arquivos de Calendário**

O módulo Aspose.Email Calendar ("ae.calendar") também fornece a funcionalidade para adicionar e recuperar informações de anexos.

- Para incluir um anexo com o compromisso, um objeto "Attachment" é criado, fornecendo o caminho do arquivo. Este anexo é, então, adicionado à lista de anexos do compromisso. O compromisso é salvo em um caminho de arquivo específico no formato iCalendar usando o método [save](https://reference.aspose.com/email/python-net/aspose.email.calendar/appointment/#methods) e o formato de arquivo apropriado.

- Para recuperar anexos de um compromisso, ele é primeiro carregado do arquivo salvo usando o método [load](https://reference.aspose.com/email/python-net/aspose.email.calendar/appointment/#methods), o número de anexos presentes em "appointment2" é exibido, e, ao iterar sobre os anexos, seus nomes são impressos.

O trecho de código abaixo demonstra como criar compromissos com anexos, salvá-los e recuperar informações de anexos usando o módulo "ae.calendar". Ele destaca a funcionalidade e as capacidades de trabalhar com compromissos e anexos em uma aplicação de calendário.

```python
import aspose.email as ae
import datetime as dt

# Adicionar um anexo a um compromisso
attendees = ae.MailAddressCollection()
attendees.append(ae.MailAddress("attendee@domain.com", "Destinatário 1"))

appointment = ae.calendar.Appointment("Sala 112", dt.datetime(2023, 5, 27), dt.date(2023, 5, 28),  ae.MailAddress("organizer@domain.com"), attendees)

attachment = ae.Attachment("D:\\Aspose\\Files\\Attachment.txt")
appointment.attachments.append(attachment)

appointment.save("D:\\Aspose\\Files\\appWithAttachments_out.ics", ae.calendar.AppointmentSaveFormat.ICS)

# Recuperar anexos de um compromisso 
appointment2 = ae.calendar.Appointment.load("D:\\Aspose\\Files\\appWithAttachments_out.ics")
print(appointment2.attachments.length)
for att in appointment2.attachments:
    print(att.name)
```
### **Status dos Destinatários de um Pedido de Reunião**
O seguinte trecho de código mostra como obter o status dos destinatários de um pedido de reunião.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-DisplayReceipientsStatusFromMeetingReqeust-DisplayReceipientsStatusFromMeetingReqeust.py" >}}

## **Converter compromisso EML para MSG preservando o Corpo em formato HTML**

A Aspose.Email torna possível converter um compromisso EML para MSG e preservar o Corpo em HTML. A propriedade "forced_rtf_body_for_appointment" da classe [MapiConversionOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiconversionoptions/#mapiconversionoptions-class) é usada para manipular o tipo do corpo do compromisso. Quando configurada como *True*, o corpo é convertido para o formato RTF por padrão. Para manter o corpo no formato HTML, deve ser definida como *False*. O seguinte exemplo de código mostra como preservar o corpo em HTML do compromisso ao convertê-lo de EML para MSG:

```python
import aspose.email as ae

eml = ae.MailMessage.load("appointment.eml")

conversionOptions = ae.mapi.MapiConversionOptions()
conversionOptions.format = ae.mapi.OutlookMessageFormat.UNICODE
# o valor padrão para ForcedRtfBodyForAppointment é true
conversionOptions.forced_rtf_body_for_appointment = False

msg = ae.mapi.MapiMessage.from_mail_message(eml, conversionOptions)

print(f"Tipo do Corpo: {msg.body_type}")

msg.save("appointment.msg")
```