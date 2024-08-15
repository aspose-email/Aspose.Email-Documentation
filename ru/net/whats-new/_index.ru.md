---
title: "Что нового в Aspose.Email для.NET"
url: /ru/net/whats-new/
weight: 5
type: docs
---


## [Электронная почта Aspose.NET 24.3](https://releases.aspose.com/email/net/release-notes/2024/aspose-email-for-net-24-3-release-notes/)

- **Поддержка контактов и календаря в MS Graph** - Методы интерфейса iGraphClient позволяют получать доступ к контактам и событиям календаря пользователей, управлять ими и взаимодействовать с ними:
  - Получите коллекцию контактов MAPI.
  - Извлеките определенный контакт.
  - Создайте новый контакт.
  - Обновите существующий контакт.
  - Получите коллекцию календарной информации.
  - Получите коллекцию элементов календаря.
  - Извлеките определенный элемент календаря.
  - Создайте новый элемент календаря.
  - Обновляет существующий элемент календаря.

## [Электронная почта Aspose.NET 24.2](https://releases.aspose.com/email/net/release-notes/2024/aspose-email-for-net-24-2-release-notes/)

- **Управление категориями элементов Outlook** - Aspose.Email позволяет извлекать и использовать цвета категорий, связанные с категориями элементов Outlook, хранящимися в файлах OLM.

- **Соответствие классам контейнеров** - новый [EnforceContainerClassMatching](https://reference.aspose.com/email/net/aspose.email.storage.pst/foldercreationoptions/enforcecontainerclassmatching/) свойство было добавлено в [FolderCreationOptions](https://reference.aspose.com/email/net/aspose.email.storage.pst/foldercreationoptions/#foldercreationoptions-class) класс, который при добавлении папки в файл PST позволяет убедиться, что класс папки соответствует ожидаемому типу или категории папок в файле PST.

## [Электронная почта Aspose для.NET 23.12](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-12-release-notes/)

- **Настройка относительного пути к ресурсам при сохранении сообщения электронной почты в формате HTML** - Aspose.Email предоставляет возможность сохранять ресурсы электронной почты с относительными путями при экспорте сообщений в формат HTML, обеспечивая повышенную гибкость при связывании ресурсов. Пользователи могут выбирать между абсолютными и относительными путями и определять собственные пути, используя [ResourceHtmlRendering](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/resourcehtmlrendering/#htmlsaveoptionsresourcehtmlrendering-event) мероприятие, упрощающее обмен и отображение электронных писем в разных системах.

## [Электронная почта Aspose для.NET 23.11](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-11-release-notes/)

- **Подтверждение сообщений электронной почты** - Добавлен набор компонентов, позволяющих пользователям проверять файлы сообщений, поддерживающие такие форматы, как eml, emlx, mht, msg и oft. Используя эту функцию, пользователи могут проверять сообщения и получать информацию о процессе проверки, включая тип формата и обнаруженные ошибки.

- **Прикрепляйте цифровые подписи к сообщениям электронной почты** - *AttachSignature* метод в [SecureEmailManager](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/#secureemailmanager-class) класс был разработан для простого добавления цифровой подписи к электронному письму.

После прикрепления подписи пользователи могут проверить результаты с помощью таких свойств, как «IsSigned», «MessageClass» и сведений о вложении.

Чтобы настроить процесс прикрепления подписи, пользователи могут использовать [SignatureOptions](https://reference.aspose.com/email/net/aspose.email/signatureoptions/#signatureoptions-class) class.

## [Электронная почта Aspose.NET 23.10](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-10-release-notes/)

- **Разделите хранилище Mbox на более мелкие части** - разделяйте большие файлы на управляемые части и выполняйте собственные действия в процессе:

  - Укажите собственный префикс для разделенных имен файлов Mbox.
  - Настройте действия до и после копирования электронного письма в новый файл Mbox.
  - Реагируйте при создании нового файла Mbox.
  - Отвечайте, когда новый файл Mbox будет заполнен электронными письмами.

- **Получите контент AlternateView от MediaType** - получить содержимое в виде строки из определенного AlternateView в сообщении электронной почты.  [MailMessage.getAlternateView Content (строковый тип носителя)](https://reference.aspose.com/email/net/aspose.email/mailmessage/getalternateviewcontent/#mailmessagegetalternateviewcontent-method) Метод позволяет получить доступ к содержимому из AlternateView, которое соответствует указанному типу носителя.

## [Электронная почта Aspose.NET 23.8](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-8-release-notes/)

- **Отправка электронных писем через Graph Client** - добавлена поддержка перегруженных методов в класс GraphClient, которые принимают объект MailMessage для отправки писем:
  - [CreateMessage (строковый идентификатор папки, сообщение MailMessage)](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/createmessage/#createmessage)

  - void [Отправить (почтовое сообщение)](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/send/#send)

- **Сохранить список рассылки Mapi в один многоконтактный файл VCF** - Сохраните список рассылки Mapi под указанным именем файла, используя предоставленные параметры сохранения. В качестве параметров можно указать имя файла и экземпляр класса MapIDistributionListSaveOptions.
  - void [Сохранить (строковое имя файла, параметры сохранения списка рассылки Mapi)](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/save/#save_5) Для этого был добавлен метод.

## [Электронная почта Aspose.NET 23.7](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-7-release-notes/)

- **Удалить элементы из PST** - Мы добавили новый метод, [Удалить элемент (идентификатор строковой записи)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/deleteitem/), в класс PersonalStorage. Этот метод позволяет удалять элементы (папки или сообщения) из персональной таблицы хранения (PST), используя уникальный идентификатор записи, связанный с элементом.
- **Обработка событий и разделение PST** - Улучшенная функциональность в [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class) class:
  - [StorageProcessingEventHandler](https://reference.aspose.com/email/net/aspose.email.storage.pst/storageprocessingeventhandler/) событие происходит до обработки хранилища, в частности перед обработкой текущего хранилища методами mergeWith или SplitInto. Это событие дает возможность выполнить собственную логику или обработать определенные операции до начала обработки хранилища.

  - [StorageProcessingEventArgs](https://reference.aspose.com/email/net/aspose.email.storage.pst/storageprocessingeventargs/) класс предоставляет данные для события PersonalStorage.StorageProcessing.

  - [Разделить на (размер длинного фрагмента, префикс имени файла строковой части, путь к строке)](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/splitinto/#splitinto_1) Метод перегрузки позволяет разделить хранилище PST на части меньшего размера.
- **Обработка календаря** - В класс CalendarReader добавлены новые свойства и метод:
  - [Count](https://reference.aspose.com/email/net/aspose.email.calendar/calendarreader/count/) Свойство позволяет получить количество компонентов (событий) Vevent, присутствующих в календаре, что упрощает отслеживание общего количества событий.
  - [IsMultiEvents](https://reference.aspose.com/email/net/aspose.email.calendar/calendarreader/ismultievents/) свойство определяет, содержит ли календарь несколько событий.
  - [Method](https://reference.aspose.com/email/net/aspose.email.calendar/calendarreader/method/) свойство получает тип метода iCalendar, связанный с объектом календаря. Оно возвращает тип метода, например «REQUEST», «PUBLISH» или «CANCEL», что позволяет получить ценную информацию о назначении календаря.
  - [Version](https://reference.aspose.com/email/net/aspose.email.calendar/calendarreader/version/) получает версию iCalendar.
  - [LoadAsMultiple()](https://reference.aspose.com/email/net/aspose.email.calendar/calendarreader/loadasmultiple/) метод позволяет загружать список событий из календаря, содержащего несколько событий. Он возвращает список объектов Appointment, что обеспечивает легкий доступ к каждому событию и его обработку в отдельности.

## [Электронная почта Aspose.NET 23.6](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-6-release-notes/)

- **Сохранить или удалить подпись при преобразовании MBOX в PST** - установите [MboxToPstConversionOptions.RemoveSignature](https://reference.aspose.com/email/net/aspose.email.storage/mboxtopstconversionoptions/removesignature/#mboxtopstconversionoptionsremovesignature-property) свойство равно 'true' для удаления подписи.
- **Удалить подпись при загрузке файлов EML** - установите [LoadOptions.RemoveSignature](https://reference.aspose.com/email/net/aspose.email/loadoptions/removesignature/) свойство равно 'true' для удаления подписи.
- **Проверка подписи электронной почты**
  - Добавлен новый [SecureEmailManager](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/) класс для проверки подписи защищенных писем. Теперь вы можете проверить подпись объектов MapiMessage и MailMessage.
  - Добавлен новый [SmimeResult](https://reference.aspose.com/email/net/aspose.email/smimeresult/) класс для хранения результатов проверки защищенной электронной почты.

  Представленные методы SecureEmailManager:

  - [Проверьте подпись (сообщение MAPI)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_3)
  - [Проверьте подпись (сообщение MAPI, сертификат X509 Certificate 2 для расшифровки)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_4)
  - [Проверьте подпись (сообщение MAPI, сертификат X509 Certificate2 для расшифровки, хранилище X509 Store)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_5)
  - [Проверьте подпись (сообщение электронной почты)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature)
  - [Проверьте подпись (сообщение электронной почты, сертификат X509 Certificate 2 для расшифровки)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_1)
  - [Проверьте подпись (сообщение электронной почты, сертификат X509 Certificate2 для расшифровки, хранилище X509 Store)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_5)

## [Электронная почта Aspose.NET 23.5](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-5-release-notes/)

- **Определите версию файлов ICS/VCS** - Используйте [Version](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/version/) собственность [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/#appointment-class) класс для получения версии файлов ICS/VCS.
- **Настройка параметров сохранения файлов vCard** - Мы добавили новое [VCardSaveOptions](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/) класс к нашему API со следующими свойствами:
  - [VCardVersion](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/version/) позволяет пользователям указывать желаемую версию vCard при сохранении контактных элементов. По умолчанию класс настроен на использование vCard версии 2.1 (vCardVersion.v21).
  - [UseExtensions](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/useextensions/) - позволяет пользователям контролировать, можно ли использовать расширенные поля при сохранении файлов vCard. Если установлено значение true (по умолчанию), расширения разрешены, что обеспечивает совместимость с настраиваемыми полями и дополнительной контактной информацией.
  - [PreferredTextEncoding](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardsaveoptions/preferredtextencoding/) - кодировка, которая будет использоваться при сохранении контактных элементов vCard.
- **Получите общее количество сообщений, содержащихся в хранилище Zimbra** с [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/gettotalitemscount/) метод [TgzReader](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/) class.
- **Извлечь подпапку PST по пути** - Извлеките подпапку с указанным именем из текущей папки PST, используя [FolderInfo.getSubfolder (строковое имя, логическое значение IgnoreCase, логическое значение HandlePathSeparator)](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getsubfolder/#getsubfolder_2) перегрузка метода.

## [Электронная почта Aspose.NET 23.4](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-4-release-notes/)

- **Добавить справочное вложение к сообщению** - Мы добавили новый [Add](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/add/#add_4) метод к [MapiAttachmentCollection](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachmentcollection/#mapiattachmentcollection-class) класс со следующими параметрами:
  - `name` - имя вложения
  - `sharedLink` - полная общедоступная ссылка на вложение, предоставленная веб-сервисом, манипулирующим вложением
  - `url` - местоположение файла
  - `providerName` - имя поставщика эталонных вложений
- **Проверка нескольких контактов vCard** - Проверьте, содержит ли исходный файл несколько контактов с новым [vCardContact.is Мультиконтакты (строковый путь к файлу)](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardcontact/ismulticontacts/#ismulticontacts_1) method.
- **Преобразование формата календаря ICS в форматы сообщений** - Преобразуйте встречи в объекты сообщений, такие как MapiMessage и MailMessage. 
- **Дополнительные возможности сохранения сообщений в форматах HTML и MHTML**:
  - [MapiTask.Priority](https://reference.aspose.com/email/net/aspose.email.mapi/mapitask/priority/) - Определяет или задает текущий приоритет объекта Task.
  - [MhtSaveOptions.SaveAllHeaders](https://reference.aspose.com/email/net/aspose.email/mhtsaveoptions/saveallheaders/) - Определяет, нужно ли сохранять все заголовки в выходном файле mhtml или нет.
  - [HtmlFormatOptions.RenderTaskFields](https://reference.aspose.com/email/net/aspose.email/htmlformatoptions/) - Указывает, что конкретные поля Задачи должны быть записаны в выходном html-файле.
- **Установите тайм-аут для процесса преобразования и загрузки сообщений** - Ограничьте время преобразования и загрузки сообщений в миллисекундах, чтобы процесс не занял больше времени, чем необходимо. Для этого были введены следующие функции:
  - [MailConversionOptions.Timeout](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/timeout/) - Ограничивает время преобразования сообщения в миллисекундах.
  - [MailConversionOptions.TimeoutReached](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/timeoutreached/) - Повышается, если время преобразования в MailMessage истекло.
  - [MsgLoadOptions.Timeout](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/timeout/) - Ограничивает время преобразования сообщения в миллисекундах.
  - [MsgLoadOptions.TimeoutReached](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/timeoutreached/) - Повышается, если время преобразования в MailMessage истекло.

## [Электронная почта Aspose.NET 23.3](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-3-release-notes/)

- **Получите общее количество сообщений, содержащихся в хранилище OLM** с [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/gettotalitemscount/) метод для [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/#olmstorage-class) class.
- **Определите, является ли MAPIMessage OFT или MSG** - Определите, был ли файл MAPImessage загружен из файла OFT или MSG вместе с новым [MapiMessage.IsTemplate](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/istemplate/) property.
- **Определите формат файла NSF**

## [Электронная почта Aspose.NET 23.1](https://releases.aspose.com/email/net/release-notes/2023/aspose-email-for-net-23-1-release-notes/)

-**Извлечение свойств сообщения из MboxMessageInfo** - Получите доступ к информации об отдельных сообщениях, хранящихся в файле mbox, например к размеру сообщения, индексу сообщения, заголовкам сообщений, флагам сообщений и другим метаданным, связанным с сообщениями. Мы добавили следующие свойства в [MboxMessageInfo](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class) class:

Дата и время — возвращает дату сообщения
Адрес электронной почты: получает адрес отправителя
строка «Тема» — возвращает тему сообщения
MailAddressCollection To — возвращает коллекцию адресов, содержащую получателей сообщения
MailAddressCollection CC — получает коллекцию адресов, содержащую получателей CC
MailAddressCollection Bcc — получает коллекцию адресов, содержащую получателей сообщений BCC

## [Электронная почта Aspose для.NET 22.12](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-12-release-notes/)

- **Получите общее количество сообщений, содержащихся в PST** - Мы добавили [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/gettotalitemscount/) метод для [PersonalStorage.Store](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/store/) property.
- **Получите стандартную папку RSS-каналов в личном хранилище**, **Добавить стандартную папку RSS-каналов в PST** - В перечисление StandardipMFolder добавлено новое значение RSSFeeds. Теперь папку RSS-каналов можно легко получить или добавить в хранилище.
- **Расшифруйте сообщение электронной почты, сохраненное в формате MAPI** - Мы добавили метод Decrypt в класс MapiMessage:
  - [MapiMessage.IsEncrypted](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/isencrypted/) - Получает значение, указывающее, зашифровано ли сообщение.
  - [MapiMessage.Decrypt()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/decrypt/#decrypt) - Расшифровывает это сообщение (метод ищет у текущего пользователя и компьютера My stores соответствующий сертификат и закрытый ключ).
  - [Сообщение MAPI. Расшифровка (сертификат X509 Certificate2)](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/decrypt/#decrypt_1) - Расшифровывает это сообщение с помощью сертификата.
- **Настройка идентификатора продукта при сохранении MapicaLendar в ICS** - Мы добавили [ProductIdentifier](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/productidentifier/) недвижимость для [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/) class.
- **Извлечение сообщений по идентификаторам из OLM и MBOX** - Это эффективный способ избежать необходимости каждый раз просматривать все хранилище в поисках определенного сообщения для извлечения.
- **Определите, является ли вложение встроенным или обычным** с [MapiAttachment.IsInline](https://reference.aspose.com/email/net/aspose.email.mapi/mapiattachment/isinline/) property.

## [Электронная почта Aspose для.NET 22.11](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-11-release-notes/)

- **Получите тип элемента MAPI** - Не проверяйте значение свойства MessageClass каждый раз перед преобразованием сообщения.
- **Удалить подпись из MapiMessage** - Для лучшей совместимости [MapiMessage.RemoveSignature](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/removesignature/) метод и [MapiMessage.IsSigned](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/issigned/) свойства были добавлены.
- **Определение предопределенных папок** - Новое [FolderInfo](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/#folderinfo-class) method, [GetPredefinedType](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/getpredefinedtype/), была введена для определения того, находится ли папка в предопределенной папке, путем возврата значения перечисления StandardipmFolder на основе указанного значения параметра.
- **Проверка формата вложения TNEF** - [Attachment.IsTnef](https://reference.aspose.com/email/net/aspose.email/attachment/istnef/) свойство указывает, является ли вложенное сообщение сообщением в формате TNEF.

## [Электронная почта Aspose для.NET 22.10](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-10-release-notes/)

- **Переименование вложения в MAPImessage** - Теперь можно редактировать [DisplayName](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/displayname/) значение свойства во вложениях MAPIMessage.

## [Электронная почта Aspose.NET 22.9](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-9-release-notes/)

- **Список сообщений с помощью Graph API** - Новое [OrderBy](https://reference.aspose.com/email/net/aspose.email.tools.search/comparisonfield/orderby/#comparisonfieldorderby-method) Метод позволяет управлять порядком полученных сообщений на основе указанных вами критериев.

## [Электронная почта Aspose.NET 22.8](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-8-release-notes/)

- **Чтение сообщений из MBOX** - Мы добавили новые функции для настройки параметров загрузки:
  - [MailStorageConverter.MboxMessageOptions](https://reference.aspose.com/email/net/aspose.email.storage/mailstorageconverter/mboxmessageoptions/) свойство - Определяет или задает параметры загрузки электронной почты при анализе хранилища Mbox.
  - [MBOXRD StorageReader. Прочитайте следующее сообщение (опции загрузки EMLO)](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxrdstoragereader/readnextmessage/#readnextmessage_1) метод. Параметр EmlloadOptions задает опции при чтении сообщения из хранилища Mbox.

## [Электронная почта Aspose.NET 22.7](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-7-release-notes/)

- **Получите идентификационную информацию о сообщении** например UID или порядковый номер с использованием следующих функций:
  - [MailboxInfo](https://reference.aspose.com/email/net/aspose.email/mailboxinfo/#mailboxinfo-class) class — представляет идентификационную информацию о сообщении в почтовом ящике.
  - [SequenceNumber](https://reference.aspose.com/email/net/aspose.email/mailboxinfo/sequencenumber/) свойство - порядковый номер сообщения.
  - [UniqueId](https://reference.aspose.com/email/net/aspose.email/mailboxinfo/uniqueid/) свойство - уникальный идентификатор сообщения.
  - [MailMessage.ItemId](https://reference.aspose.com/email/net/aspose.email/mailmessage/itemid/) свойство — представляет идентификационную информацию о сообщении в почтовом ящике.

## [Электронная почта Aspose.NET 22.6](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-6-release-notes/)

- **Сохранение исходной метки времени в файлах ICS** - Извлеките элементы календаря из файлов PST и сохраните их в формате ICS с исходной отметкой времени, используя следующие опции:
  - [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/) - Позволяет указать дополнительные параметры при сохранении MapiCalendar в формате ICS.
  - [MapiCalendarIcsSaveOptions.KeepOriginalDateTimeStamp](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/keeporiginaldatetimestamp/) - Позволяет сохранить исходное значение DateTimestamp в выходном файле.

## [Электронная почта Aspose.NET 22.5](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-5-release-notes/)

- **Перечисление сообщений с поддержкой пейджинга через Graph Client** - API обеспечивает поддержку разбиения на страницы и фильтрации сообщений со списком. Это очень удобно в тех случаях, когда в почтовом ящике находится большое количество сообщений и для получения сводной информации о них требуется много времени.
- **Асинхронный режим работы с почтовыми клиентами** - Новый подход к задаче включает следующих членов API:
  - [`IAsyncSmtpClient`](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/) - Позволяет приложениям отправлять сообщения с использованием простого протокола передачи почты (SMTP).
  - [`SmtpClient.CreateAsync`](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/createasync/#smtpclientcreateasync-method) - Создает новый экземпляр `Aspose.Email.Clients.Smtp.SmtpClient` class.
  - [`IAsyncSmtpClient.SendAsync`](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/sendasync/)(`Aspose.Email.Clients.Smtp.Models.SmtpSend`) набор параметров метода.
  - [`IAsyncSmtpClient.ForwardAsync`](https://reference.aspose.com/email/net/aspose.email.clients.smtp/iasyncsmtpclient/forwardasync/)(`Aspose.Email.Clients.Smtp.Models.SmtpForward`) аргументы.
  - [`IAsyncImapClient`](https://reference.aspose.com/email/net/aspose.email.clients.imap/iasyncimapclient/#iasyncimapclient-interface) - Позволяет приложениям получать доступ к сообщениям и управлять ими с помощью протокола доступа к сообщениям Интернета (IMAP).
  - [`ImapClient.CreateAsync`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/createasync/) - Создает новый экземпляр `Aspose.Email.Clients.Imap.ImapClient` class.

## [Электронная почта Aspose.NET 22.4](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-4-release-notes/)

- **Отправка электронной почты с помощью служб доставки MailGun и SendGrid** - Мы создали унифицированный API, который можно использовать для инициализации опций в зависимости от того, какой сервис будет использоваться для отправки сообщений, вызова нужного экземпляра клиента с помощью конструктора, подготовки и отправки сообщения электронной почты. Существует также асинхронная версия метода Send.
- **Установите заголовок X-ALT-DESC в файле ICS** - Мы представили новый [HtmlDescription](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/htmldescription/#appointmenthtmldescription-property) свойство для установки заголовка X-ALT-DESC.

## [Электронная почта Aspose.NET 22.3](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-3-release-notes/)

- **Список вложений сообщений с помощью клиента IMAP** - Получайте информацию о вложениях, такую как имя, размер, без извлечения данных вложения. Участники API, участвующие в операции:
  - [`Aspose.Email.Clients.Imap.ImapAttachmentInfo`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapattachmentinfo/) - Представляет собой информацию о вложении.
  - [`Aspose.Email.Clients.Imap.ImapAttachmentInfoCollection`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapattachmentinfocollection/) - Представляет собой коллекцию IMapAttachmentInfo.
  - [`Aspose.Email.Clients.Imap.ListAttachments(int sequenceNumber)`](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/listattachments/) - Получает информацию о каждом вложении в сообщении.
- **Получайте товары с вложениями через клиент EWS** - Мы добавили [`FetchItems(EwsFetchItems options)`](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/fetchitems/#iewsclientfetchitems-method) метод для [EwsClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/iewsclient/#iewsclient-interface). Он принимает экземпляр [EwsFetchItems](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice.models/ewsfetchitems/#ewsfetchitems-class) класс в качестве параметра для управления поведением метода.

## [Электронная почта Aspose.NET 22.2](https://releases.aspose.com/email/net/release-notes/2022/aspose-email-for-net-22-2-release-notes/)

- **Добавление справочных вложений**
    Представленные члены API:
  - [`Aspose.Email.ReferenceAttachment`](https://reference.aspose.com/email/net/aspose.email/referenceattachment/#referenceattachment-class) - представляет собой справочное приложение.
  - [`Aspose.Email.AttachmentPermissionType`](https://reference.aspose.com/email/net/aspose.email/attachmentpermissiontype/) - Данные типа разрешения, связанные с вложением веб-ссылки.
  - [`Aspose.Email.AttachmentProviderType`](https://reference.aspose.com/email/net/aspose.email/attachmentprovidertype/) - Тип веб-сервиса, манипулирующего вложением.
- **Извлечь класс сообщения** - Мы добавили [MessageClass](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/messageclass/#exchangemessageinfomessageclass-propertyм) недвижимость для [ExchangeMessageInfo](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangemessageinfo/#exchangemessageinfo-class) класс для извлечения класса каждого сообщения в коллекции из общей папки после установки соединения с клиентом EWS.
