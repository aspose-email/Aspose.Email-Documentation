---
title: "Что нового в Aspose.Email для .NET"
url: /ru/net/whats-new/
weight: 5
type: docs
---


## [Aspose.Email для .NET 24.3](https://releases.aspose.com/email/net/release-notes/2024/aspose-email-for-net-24-3-release-notes/)

- **Поддержка контактов и календаря в MS Graph** - Методы интерфейса IGraphClient позволяют получать доступ, управлять и взаимодействовать с контактами и событиями календаря пользователей:
  - Получить коллекцию MAPI-контактов.
  - Получить конкретный контакт.
  - Создать новый контакт.
  - Обновить существующий контакт.
  - Получить коллекцию информации о календаре.
  - Получить коллекцию элементов календаря.
  - Получить конкретный элемент календаря.
  - Создать новый элемент календаря.
  - Обновить существующий элемент календаря.

## [Aspose.Email для .NET 24.2](https://releases.aspose.com/email/net/release-notes/2024/aspose-email-for-net-24-2-release-notes/)

- **Управление категориями элементов Outlook** - Aspose.Email позволяет получать и использовать цвета категорий, связанные с категориями элементов Outlook, хранящимися в файлах OLM.

- **Соответствие класса контейнера** - В класс [FolderCreationOptions](https://reference.aspose.com/email/net/aspose.email.storage.pst/foldercreationoptions/#foldercreationoptions-class) добавлено новое свойство [EnforceContainerClassMatching](https://reference.aspose.com/email/net/aspose.email.storage.pst/foldercreationoptions/enforcecontainerclassmatching/), которое при добавлении папки в файл PST позволяет гарантировать соответствие класса папки ожидаемому типу или категории папок внутри файла PST.

## [Aspose.Email для .NET 23.12](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-12-release-notes/)

- **Установка относительного пути к ресурсам при сохранении сообщения электронной почты в формате HTML** - Aspose.Email вводит возможность сохранения ресурсов электронной почты с относительными путями при экспорте сообщений в формат HTML, предлагая улучшенную гибкость для связывания ресурсов. Пользователи могут выбирать между абсолютными и относительными путями, а также определять собственные пути с помощью события [ResourceHtmlRendering](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/resourcehtmlrendering/#htmlsaveoptionsresourcehtmlrendering-event), упрощая обмен и отображение электронной почты через различные системы.

## [Aspose.Email для .NET 23.11](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-11-release-notes/)

- **Проверка сообщений электронной почты** - Введён набор компонентов, который позволяет пользователям проверять файлы сообщений, поддерживая форматы такие как eml, emlx, mht, msg и oft. Используя эту функциональность, пользователи могут проверять сообщения и получать информацию о процессе проверки, включая тип формата и возникшие ошибки.

- **Присоединение цифровых подписей к сообщениям электронной почты** - Метод *AttachSignature* в классе [SecureEmailManager](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/#secureemailmanager-class) был разработан для легкого добавления цифровой подписи к электронной почте.

После того как подпись была прикреплена, пользователи могут проверять результаты через свойства 'IsSigned', 'MessageClass' и детали вложения.

Чтобы настроить процесс прикрепления подписи, пользователи могут использовать класс [SignatureOptions](https://reference.aspose.com/email/net/aspose.email/signatureoptions/#signatureoptions-class).

## [Aspose.Email для .NET 23.10](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-10-release-notes/)

- **Разделение хранения Mbox на меньшие части** - разделите большие файлы на управляемые части и реализуйте настраиваемые действия в процессе:

  - Укажите собственный префикс для имен разделенных файлов Mbox.
  - Настройте действия до и после копирования электронного письма в новый файл Mbox.
  - Реагируйте при создании нового файла Mbox.
  - Ответьте, когда новый файл Mbox заполнен электронными письмами.

- **Получить содержимое AlternateView по MediaType** - извлеките содержимое в виде строки из конкретного AlternateView в сообщении электронной почты. Метод [MailMessage.GetAlternateViewContent(string mediaType)](https://reference.aspose.com/email/net/aspose.email/mailmessage/getalternateviewcontent/#mailmessagegetalternateviewcontent-method) позволяет получить доступ к содержимому из AlternateView, который соответствует указанному типу медиа.

## [Aspose.Email для .NET 23.8](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-8-release-notes/)

- **Отправка электронных писем через Graph Client** - добавлена поддержка перегруженных методов в класс GraphClient, которые принимают объект MailMessage для отправки электронных писем:
  - [CreateMessage(string folderId, MailMessage message)](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createmessage/#createmessage)

  - void [Send(MailMessage message)](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/send/#send)

- **Сохранение списка распределения Mapi в один файл VCF с несколькими контактами** - Сохраните список распределения Mapi в указанном имени файла с использованием предоставленных параметров сохранения. Вы можете предоставить имя файла и экземпляр класса MapiDistributionListSaveOptions в качестве параметров.
  - Метод void [Save(string fileName, MapiDistributionListSaveOptions options)](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/save/#save_5) был добавлен для этой цели.

## [Aspose.Email для .NET 23.7](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-7-release-notes/)

- **Удаление элементов из PST** - Мы добавили новый метод, [DeleteItem(string entryId)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/deleteitem/), в класс PersonalStorage. Этот метод предоставляет способ удалить элементы (папки или сообщения) из таблицы персонального хранения (PST) с использованием уникального идентификатора entryId, связанного с элементом.
- **Обработка событий и разделение PST** - Улучшенная функциональность в классе [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class):
  - Событие [StorageProcessingEventHandler](https://reference.aspose.com/email/net/aspose.email.storage.pst/storageprocessingeventhandler/) происходит до обработки хранилища, в частности, перед обработкой текущего хранилища в методах MergeWith или SplitInto. Это событие предоставляет возможность выполнить пользовательскую логику или обработать определенные операции перед началом обработки хранилища.

  - Класс [StorageProcessingEventArgs](https://reference.aspose.com/email/net/aspose.email.storage.pst/storageprocessingeventargs/) предоставляет данные для события PersonalStorage.StorageProcessing. 

  - Перегруженный метод [SplitInto(long chunkSize, string partFileNamePrefix, string path)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/splitinto/#splitinto_1) позволяет разделить хранилище PST на части меньшего размера. 
- **Обработка календаря** - Новые свойства и метод были добавлены в класс CalendarReader:
  - Свойство [Count](https://reference.aspose.com/email/net/aspose.email.calendar/calendarreader/count/) позволяет получить количество компонентов Vevent (событий), присутствующих в календаре, что упрощает отслеживание общего количества событий.
  - Свойство [IsMultiEvents](https://reference.aspose.com/email/net/aspose.email.calendar/calendarreader/ismultievents/) определяет, содержит ли календарь несколько событий.
  - Свойство [Method](https://reference.aspose.com/email/net/aspose.email.calendar/calendarreader/method/) получает тип метода iCalendar, связанный с объектом календаря. Оно возвращает тип метода, такой как "REQUEST", "PUBLISH" или "CANCEL", предоставляя ценную информацию о цели календаря.
  - Свойство [Version](https://reference.aspose.com/email/net/aspose.email.calendar/calendarreader/version/) получает версию iCalendar.
  - Метод [LoadAsMultiple()](https://reference.aspose.com/email/net/aspose.email.calendar/calendarreader/loadasmultiple/) позволяет загружать список событий из календаря, содержащего несколько событий. Он возвращает список объектов Appointment, позволяя легко получать доступ и обрабатывать каждое событие по отдельности.

## [Aspose.Email для .NET 23.6](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-6-release-notes/)

- **Сохранение или удаление подписи при конвертации MBOX в PST** - установите свойство [MboxToPstConversionOptions.RemoveSignature](https://reference.aspose.com/email/net/aspose.email.storage/mboxtopstconversionoptions/removesignature/#mboxtopstconversionoptionsremovesignature-property) в 'true', чтобы удалить подпись.
- **Удаление подписи при загрузке EML файлов** - установите свойство [LoadOptions.RemoveSignature](https://reference.aspose.com/email/net/aspose.email/loadoptions/removesignature/) в 'true', чтобы удалить подпись.
- **Проверка подписи электронной почты**
  - Добавлен новый класс [SecureEmailManager](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/) для проверки подписи защищенных электронных писем. Теперь вы можете проверить подпись объектов MapiMessage и MailMessage.
  - Добавлен новый класс [SmimeResult](https://reference.aspose.com/email/net/aspose.email/smimeresult/) для хранения результатов проверки защищенных электронных писем.

  Введены методы SecureEmailManager:

  - [CheckSignature(MapiMessage msg)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_3) 
  - [CheckSignature(MapiMessage msg, X509Certificate2 certificateForDecrypt)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_4) 
  - [CheckSignature(MapiMessage msg, X509Certificate2 certificateForDecrypt, X509Store store)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_5) 
  - [CheckSignature(MailMessage msg)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature) 
  - [CheckSignature(MailMessage msg, X509Certificate2 certificateForDecrypt)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_1) 
  - [CheckSignature(MailMessage msg, X509Certificate2 certificateForDecrypt, X509Store store)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_5)

## [Aspose.Email для .NET 23.5](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-5-release-notes/)

- **Определение версии файлов ICS/VCS** - Используйте свойство [Version](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/version/) класса [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) для получения версии файлов ICS/VCS.
- **Настройка параметров сохранения для файлов VCard** - Мы добавили новый класс [VCardSaveOptions](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/) в наш API со следующими свойствами:
  - Свойство [VCardVersion](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/version/) позволяет пользователям указывать желаемую версию vCard при сохранении контактных элементов. По умолчанию класс настроен на использование версии vCard 2.1 (VCardVersion.V21).
  - Свойство [UseExtensions](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/useextensions/) - позволяет пользователям контролировать, могут ли использоваться расширенные поля при сохранении файлов vCard. Когда установлено в true (по умолчанию), разрешены расширения, что обеспечивает совместимость с настраиваемыми полями и дополнительной информацией о контактах.
  - Свойство [PreferredTextEncoding](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/preferredtextencoding/) - кодировка, которая будет использоваться при сохранении элементов контактов vCard.
- **Получить общее количество элементов сообщений, содержащихся в хранилище Zimbra**, с помощью метода [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/gettotalitemscount/) класса [TgzReader](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/).
- **Извлечение подкаталога PST по пути** - Получите подкаталог с указанным именем из текущей папки PST, используя перегруженный метод [FolderInfo.GetSubFolder(string name, bool ignoreCase, bool handlePathSeparator)](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getsubfolder/#getsubfolder_2).

## [Aspose.Email для .NET 23.4](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-4-release-notes/)

- **Добавление ссылки во вложение сообщения** - Мы добавили новый метод [Add](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/add/#add_4) к классу [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/#mapiattachmentcollection-class) со следующими параметрами:
  - `name` - имя вложения
  - `sharedLink` - полностью квалифицированная общая ссылка на вложение, предоставленная веб-сервисом, манипулирующим вложением
  - `url` - местоположение файла
  - `providerName` - имя провайдера ссылочного вложения
- **Проверка нескольких контактов VCard** - Проверьте, содержит ли исходный файл несколько контактов с помощью нового метода [VCardContact.IsMultiContacts(string filePath)](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardcontact/ismulticontacts/#ismulticontacts_1).
- **Преобразование календаря формата ICS в форматы сообщения** - Преобразование встреч в объекты сообщения, такие как MapiMessage и MailMessage.  
- **Дополнительные параметры для сохранения сообщений в HTML и MHTML форматах**:
  - Свойство [MapiTask.Priority](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/priority/) - Получает или устанавливает текущий приоритет объекта задачи.
  - Свойство [MhtSaveOptions.SaveAllHeaders](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/saveallheaders/) - Определяет, необходимо ли сохранять все заголовки в выходном файле mhtml или нет.
  - Свойство [HtmlFormatOptions.RenderTaskFields](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/) - Указывает, что конкретные поля задачи должны быть записаны в выходном html.
- **Установка таймаута для процесса конвертации и загрузки сообщений** - Ограничьте время в миллисекундах, пока конвертируете и загружаете сообщения, чтобы обеспечить, чтобы процесс не занимал дольше необходимого времени. Для этой цели были введены следующие функции:
  - Свойство [MailConversionOptions.Timeout](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/timeout/) - Ограничивает время в миллисекундах при конвертации сообщения.
  - Свойство [MailConversionOptions.TimeoutReached](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/timeoutreached/) - Возникает, если время вышло при конвертации в MailMessage.
  - Свойство [MsgLoadOptions.Timeout](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/timeout/) - Ограничивает время в миллисекундах при конвертации сообщения.
  - Свойство [MsgLoadOptions.TimeoutReached](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/timeoutreached/) - Возникает, если время вышло при конвертации в MailMessage.

## [Aspose.Email для .NET 23.3](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-3-release-notes/)

- **Получить общее количество элементов сообщений, содержащихся в хранилище OLM**, с помощью метода [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/gettotalitemscount/) класса [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/#olmstorage-class).
- **Определение, является ли MapiMessage OFT или MSG** - Определите, загружался ли MapiMessage из файла OFT или MSG с помощью нового свойства [MapiMessage.IsTemplate](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/istemplate/).
- **Обнаружение формата файла NSF**

## [Aspose.Email для .NET 23.1](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-1-release-notes/)

- **Извлечение свойств сообщения из MboxMessageInfo** - Получите доступ к информации о отдельных сообщениях, хранящихся в файле mbox, таких как размер сообщения, индекс сообщения, заголовки сообщения, флаги сообщения и другие метаданные, связанные с сообщениями. Мы добавили следующие свойства в класс [MboxMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class):

DateTime Date - Получает дату сообщения
MailAddress From - Получает адрес отправителя
string Subject - Получает тему сообщения
MailAddressCollection To - Получает коллекцию адресов, содержащую получателей сообщения
MailAddressCollection CC - Получает коллекцию адресов, содержащую адресаты CC
MailAddressCollection Bcc - Получает коллекцию адресов, содержащую адресаты BCC сообщения

## [Aspose.Email для .NET 22.12](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-12-release-notes/)

- **Получение общего количества элементов сообщений, содержащихся в PST** - Мы добавили метод [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/gettotalitemscount/) к свойству [PersonalStorage.Store](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/store/).
- **Получение стандартной папки RSS лент в персональном хранилище**, **Добавление стандартной папки RSS лент в PST** - Новое значение RssFeeds было добавлено к перечислению StandardIpmFolder. Теперь папку RSS лент можно легко извлечь или добавить в хранилище.
- **Дешифрование сообщения электронной почты, хранящегося в формате MAPI** - Мы добавили метод Decrypt в класс MapiMessage:
  - Свойство [MapiMessage.IsEncrypted](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/isencrypted/) - Получает значение, указывающее, зашифровано ли сообщение.
  - Метод [MapiMessage.Decrypt()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/decrypt/#decrypt) - Дешифрует это сообщение (метод ищет текущего пользователя и хранилища компьютера для соответствующего сертификата и закрытого ключа).
  - Метод [MapiMessage.Decrypt(X509Certificate2 certificate)](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/decrypt/#decrypt_1) - Дешифрует это сообщение с сертификатом. 
- **Установка идентификатора продукта при сохранении MapiCalendar в ICS** - Мы добавили свойство [ProductIdentifier](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/productidentifier/) к классу [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/). 
- **Извлечение сообщений по идентификаторам из OLM и MBOX** - Это эффективный способ избежать обхода всего хранилища каждый раз, чтобы найти конкретное сообщение для извлечения.
- **Определение того, является ли вложение встроенным или обычным** с помощью свойства [MapiAttachment.IsInline](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/isinline/).

## [Aspose.Email для .NET 22.11](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-11-release-notes/)

- **Получение типа элемента MAPI** - Избегайте проверки значения свойства MessageClass каждый раз перед конвертацией сообщения.
- **Удаление подписи из MapiMessage** - Для лучшей совместимости были добавлены метод [MapiMessage.RemoveSignature](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/removesignature/) и свойство [MapiMessage.IsSigned](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/issigned/).
- **Идентификация предопределенных папок** - Новый метод [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/#folderinfo-class) - [GetPredefinedType](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getpredefinedtype/) был введён для определения, находится ли папка в предопределенной папке, возвращая значение перечисления StandardIpmFolder на основе указанного параметра.
- **Проверка формата вложения TNEF** - Свойство [Attachment.IsTnef](https://reference.aspose.com/email/net/aspose.email/attachment/istnef/) указывает, является ли вложение сообщения форматом TNEF.

## [Aspose.Email для .NET 22.10](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-10-release-notes/)

- **Переименование вложения в MapiMessage** - Теперь можно редактировать значение свойства [DisplayName](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/displayname/) во вложениях MapiMessage.

## [Aspose.Email для .NET 22.9](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-9-release-notes/)

- **Список сообщений с использованием Graph API** - Новый метод [OrderBy](https://reference.aspose.com/email/net/aspose.email.tools.search/comparisonfield/orderby/#comparisonfieldorderby-method) позволяет контролировать порядок извлеченных сообщений на основе указанных вами критериев.

## [Aspose.Email для .NET 22.8](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-8-release-notes/)

- **Чтение сообщений из MBOX** - Мы представили новые функции для настройки параметров загрузки:
  - Свойство [MailStorageConverter.MboxMessageOptions](https://reference.aspose.com/email/net/aspose.email.storage/mailstorageconverter/mboxmessageoptions/) - Получает или устанавливает параметры загрузки электронной почты при анализе хранилища Mbox.
  - Метод [MboxrdStorageReader.ReadNextMessage(EmlLoadOptions options)](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/readnextmessage/#readnextmessage_1). Параметр EmlLoadOptions задает параметры при чтении сообщения из хранилища Mbox.

## [Aspose.Email для .NET 22.7](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-7-release-notes/)

- **Получение информации об идентификации сообщения**, такой как UID или номер последовательности, с помощью следующих функций:
  - Класс [MailboxInfo](https://reference.aspose.com/email/net/aspose.email/mailboxinfo/#mailboxinfo-class) - представляет информацию об идентификации сообщения в почтовом ящике.
  - Свойство [SequenceNumber](https://reference.aspose.com/email/net/aspose.email/mailboxinfo/sequencenumber/) - номер последовательности сообщения.
  - Свойство [UniqueId](https://reference.aspose.com/email/net/aspose.email/mailboxinfo/uniqueid/) - уникальный идентификатор сообщения.
  - Свойство [MailMessage.ItemId](https://reference.aspose.com/email/net/aspose.email/mailmessage/itemid/) - представляет информацию об идентификации сообщения в почтовом ящике.

## [Aspose.Email для .NET 22.6](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-6-release-notes/)

- **Сохранение оригинальной временной метки в файлах ICS** - Извлекайте элементы календаря из файлов PST и сохраняйте их в формате ICS с оригинальной временной меткой, используя следующие параметры:
  - Класс [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/) - Позволяет указывать дополнительные параметры при сохранении MapiCalendar в формате ICS.
  - Свойство [MapiCalendarIcsSaveOptions.KeepOriginalDateTimeStamp](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/keeporiginaldatetimestamp/) - Позволяет сохранить оригинальное значение DateTimeStamp в выходном файле.