---
title: "Trabalhando com Itens de Calendário em Arquivo PST"
url: /pt/python-net/trabalhando-com-itens-de-calendario-em-arquivo-pst/
weight: 50
type: docs
---


## **Adicionando MapiCalendar ao PST**
Criar um Novo Arquivo PST e Adicionar Subpastas mostrou como criar um arquivo PST e adicionar uma subpasta a ele. Com Aspose.Email, você pode adicionar MapiCalendar à subpasta Calendário de um arquivo PST que você criou ou carregou. Abaixo estão os passos para adicionar MapiCalendar a um PST:

1. Crie um objeto MapiCalendar.
1. Defina as propriedades do MapiCalendar usando um construtor e métodos.
1. Crie um PST usando o método PersonalStorage.create().
1. Crie uma pasta pré-definida (Calendário) na raiz do arquivo PST acessando a pasta raiz e, em seguida, chamando o método add_mapi_message_item().

O seguinte snippet de código mostra como criar um MapiCalendar e depois adicioná-lo à pasta de calendário de um arquivo PST recém-criado.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMapiCalendarToPST-AddMapiCalendarToPST.py" >}}
## **Salvar Itens de Calendário do PST em Disco no Formato ICS**
Este artigo mostra como acessar itens de calendário de um arquivo PST do Outlook e salvar o calendário em disco no formato ICS. Use as classes PersonalStorage e MapiCalendar para obter as informações do calendário. Abaixo estão os passos para salvar itens de calendário:

1. Carregue o arquivo PST na classe PersonalStorage.
1. Navegue até a pasta Calendário.
1. Obtenha o conteúdo da pasta Calendário para obter a coleção de mensagens.
1. Percorra a coleção de mensagens.
1. Chame o método PersonalStorage.extract_message() para obter as informações de contato na classe MapiCalendar.
1. Chame o método MapiCalendar.save() para salvar o item de calendário em disco no formato ICS.

O programa abaixo carrega um arquivo PST do disco e salva todos os itens de calendário no formato ICS. Os arquivos ICS podem então ser usados em qualquer outro programa que possa carregar o arquivo padrão de calendário ICS. Aberto no Microsoft Outlook, um arquivo ICS se parece com o da captura de tela abaixo.

|![todo:image_alt_text](working-with-calendar-items-in-pst-file_1.png)|
| :- |
O seguinte snippet de código mostra como exportar os itens de calendário do PST do Outlook para o formato ICS.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-SaveCalendarItems-SaveCalendarItems.py" >}}

### **Salvando como ICS com Timestamp Original**

O método *keep_original_date_time_stamp* da classe [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapicalendaricssaveoptions/#mapicalendaricssaveoptions-class) permite preservar as marcas de data e hora originais dos itens de calendário ao salvá-los como um arquivo ICS (iCalendar). O seguinte exemplo de código demonstra a implementação deste método:

```python
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

calendar_folder = pst.get_predefined_folder(ae.storage.pst.StandardIpmFolder.APPOINTMENTS)

for msg_info in calendar_folder.enumerate_messages():
    cal = pst.extract_message(msg_info).to_mapi_message_item()

    save_options = ae.mapi.MapiCalendarIcsSaveOptions()
    save_options.keep_original_date_time_stamp = True

    if not (cal is None):
      cal.save("cal.ics", save_options)
```
## **Modificar/Excluir Ocorrências de Recorrências**

Exceções podem ser adicionadas a recorrências existentes usando a API Aspose.Email para .NET. O exemplo de código a seguir ilustra o uso desse recurso.  

```py
from datetime import datetime, timedelta
from aspose.email.storage.pst import PersonalStorage, StandardIpmFolder, FileFormatVersion
from aspose.email.mapi import MapiCalendar, MapiCalendarEventRecurrence, \
    MapiCalendarDailyRecurrencePattern, MapiCalendarRecurrenceEndType, \
    MapiCalendarExceptionInfo, MapiCalendarRecurrencePatternType, \
    MapiRecipientCollection, MapiRecipientType

start_date = datetime.now().date()

recurrence = MapiCalendarEventRecurrence()
pattern = MapiCalendarDailyRecurrencePattern()
pattern.pattern_type = MapiCalendarRecurrencePatternType.DAY
pattern.period = 1
pattern.end_type = MapiCalendarRecurrenceEndType.NEVER_END
recurrence.recurrence_pattern = pattern

exception_date = start_date + timedelta(days=1)

# adicionando uma exceção
exception_info = MapiCalendarExceptionInfo()
exception_info.location = "Londres"
exception_info.subject = "Subj"
exception_info.original_start_date = exception_date
exception_info.start_date_time = exception_date
exception_info.end_date_time = exception_date + timedelta(hours=5)
pattern.exceptions.append(exception_info)
pattern.modified_instance_dates.append(exception_date)
# cada instância modificada também deve ter uma entrada no campo DeletedInstanceDates com a data da instância original.
pattern.deleted_instance_dates.append(exception_date)

# adicionando uma instância excluída
pattern.deleted_instance_dates.append(exception_date + timedelta(days=2))

rec_coll = MapiRecipientCollection()
rec_coll.add("receiver@domain.com", "receiver", MapiRecipientType.TO)
new_cal = MapiCalendar(
    "Este é o Local",
    "Este é o Resumo",
    "Este é um teste de recorrência",
    start_date,
    start_date + timedelta(hours=3),
    "organizer@domain.com",
    rec_coll
)
new_cal.recurrence = recurrence

with PersonalStorage.create("output.pst", FileFormatVersion.UNICODE) as pst:
    calendar_folder = pst.create_predefined_folder("Calendário", StandardIpmFolder.APPOINTMENTS)
    calendar_folder.add_message(new_cal)
```