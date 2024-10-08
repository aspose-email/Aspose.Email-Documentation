---
title: "Почему автоматизация не лучший выбор"
url: /ru/net/why-not-automation/
weight: 40
type: docs
---

Почему компоненты Aspose являются гораздо лучшим вариантом по сравнению с автоматизацией Microsoft Office. Есть два вопроса, которые мы слышим чаще всего здесь, в Aspose:

1. **Требуют ли ваши продукты установки Microsoft Office для их работы?**  
   Простой ответ - нет. Компоненты Aspose полностью независимы и не связаны с Microsoft Corporation, не имеют ее авторизации, спонсорства или любого другого одобрения.
2. **Почему мы должны использовать продукты Aspose, а не автоматизацию Microsoft Office?**  
   Кратчайший ответ, который мы можем дать, заключается в том, что есть множество причин, основная из которых - это то, что сама Microsoft настоятельно не рекомендует автоматизацию Office с помощью программных решений: [Рекомендации по серверной автоматизации Office](https://support.microsoft.com/?scid=kb;EN-US;q257757). Есть несколько причин, почему компоненты Aspose являются лучшей альтернативой автоматизации. Некоторые ключевые моменты описаны ниже. Также не забудьте посетить ссылки в конце этого раздела.

## **Безопасность**

Следующее является прямой цитатой из вышеуказанной статьи Microsoft:

_"Приложения Office никогда не предназначались для использования на стороне сервера, и поэтому не учитывают проблемы безопасности, с которыми сталкиваются распределенные компоненты. Office не аутентифицирует входящие запросы и не защищает вас от непреднамеренного запуска макросов или запуска другого сервера, который может выполнять макросы, из вашего серверного кода. Не открывайте файлы, загружаемые на сервер от анонимного веб! Исходя из настроек безопасности, которые были установлены последними, сервер может выполнять макросы под учетной записью администратора или системной учетной записью с полными привилегиями и скомпрометировать вашу сеть! Кроме того, Office использует много компонентов на стороне клиента (например, Simple MAPI, WinInet и MSDAIPP), которые могут кэшировать информацию для аутентификации клиента, чтобы ускорить обработку. Если Office автоматизируется на стороне сервера, один экземпляр может обслуживать более одного клиента, и поскольку информация для аутентификации была закэширована для этой сессии, возможно, что один клиент может использовать закэшированные учетные данные другого клиента, получая тем самым несанкционированные права доступа, выдавая себя за других пользователей."_

Продукты Aspose очень безопасны. Компоненты Aspose работают в том же пользовательском контексте, что и все ASP.NET приложения, под пользователем ASPNET. Следовательно, компоненты Aspose не представляют потенциальной угрозы для жизненно важных системных ресурсов. Более того, когда документ открывается компонентом Aspose, макросы не выполняются автоматически. Компоненты Aspose были созданы с целью позволить разработчикам создавать, манипулировать и сохранять файлы Office. Ни один из рисков, связанных с пакетом Microsoft Office, не является присущим компонентам Aspose.

## **Стабильность**

Следующее является прямой цитатой из вышеуказанной статьи Microsoft:

_"Office 2000, Office XP и Office 2003 используют технологию Microsoft Windows Installer (MSI) для облегчения установки и самовосстановления для конечного пользователя. MSI вводит концепцию "установки при первом использовании", которая позволяет динамически устанавливать или настраивать функции во время выполнения (для системы или, чаще, для конкретного пользователя). В среде на стороне сервера это как замедляет производительность, так и увеличивает вероятность появления диалогового окна, которое запрашивает у пользователя одобрение установки или предоставление соответствующего установочного диска. Хотя это и задумано для повышения устойчивости Office как продукта для конечного пользователя, реализация возможностей MSI в Office является контрпродуктивной в среде на стороне сервера. Более того, стабильность Office в целом не может быть гарантирована при запуске на стороне сервера, потому что он не был спроектирован или протестирован для такого использования. Использование Office в качестве сервисного компонента на сетевом сервере может снизить стабильность этой машины и, как следствие, вашей сети в целом. Если вы планируете автоматизировать Office на стороне сервера, попытайтесь изолировать программу на выделенном компьютере, который не может повлиять на критические функции и который может быть перезапущен по мере необходимости."_

Поскольку компоненты Aspose упакованы в единый DLL, никогда не потребуется установка каких-либо дополнительных частей или компонентов для их функционирования. Компоненты Aspose используются только приложениями .NET, и в коде компонента нет частей, предназначенных для ожидания ответа человека. Компоненты Aspose были тщательно протестированы. Компоненты Aspose используются такими компаниями, как IBM, Hilton, Reader's Digest, Bank of America и многими другими.

## **Масштабируемость/Скорость**

Следующее является прямой цитатой из вышеуказанной статьи Microsoft:

_"Компоненты на стороне сервера должны быть высокореверсивными, многопоточными COM-компонентами с минимальными накладными расходами и высокой пропускной способностью для нескольких клиентов. Приложения Office во всех отношениях являются точной противоположностью. Они не реверсивны, основаны на STA, и предназначены для предоставления разнообразной, но ресурсоемкой функциональности для одного клиента. Они предлагают мало масштабируемости как решение на стороне сервера и имеют фиксированные ограничения на важные элементы, такие как память, которые нельзя изменить через конфигурацию. Более важно, они используют глобальные ресурсы (такие как файлы с адресами в памяти, глобальные надстройки или шаблоны и общие серверы автоматизации), что может ограничить количество экземпляров, которые могут работать одновременно и привести к состояниям гонки, если они настроены в многоклиентской среде. Разработчики, планирующие запустить более одного экземпляра любого приложения Office одновременно, должны учитывать "пул" или сериализацию доступа к приложению Office, чтобы избежать потенциальных взаимных блокировок или повреждения данных."_

Компоненты Aspose высоко масштабируемы и молниеносны. Приложения Office не были предназначены для использования одновременно сотнями и тысячами пользователей; однако компоненты Aspose были созданы именно для этого. Наши компоненты являются истинным решением .NET и работают безупречно как на одном сервере, обеспечивающем одно приложение, так и на балансируемой веб-ферме, обеспечивающей приложение для всей компании.

## **Цена**

Когда приложение использует автоматизацию Microsoft Office, копия Microsoft Office должна быть приобретена для каждой машины, на которой работает приложение. Часто приложение может потребовать создания или манипуляции офисным файлом, но не требует от пользователя наличия Office. Aspose предлагает очень экономичную, безроялтную лицензию на перераспределение, которая позволит развернуть приложение для неограниченного числа пользователей без забот о лицензировании.

При создании веб-приложений важно знать, что компоненты автоматизации Microsoft Office не имеют ценовой политики и лицензирования для решений на стороне сервера ([Лицензирование веб-компонентов Office 2000 и расширений Office Server](https://support.microsoft.com/?scid=kb;EN-US;q243006)); поэтому нет хорошего решения по лицензированию для развертывания веб-приложений, которые используют компоненты Microsoft Office. Aspose также предлагает очень экономичное решение для серверных приложений.

## **Функции**

Компоненты Aspose обеспечивают всё необходимое для управления офисными файлами, плюс много, много другого. Они разработаны с философией, позволяющей разработчикам добиваться наилучших результатов с минимальным объемом работы. В отличие от автоматизации Office, компоненты Aspose предоставляют множество мощных функций, экономящих время. Например, Aspose.Cells предоставляет разработчикам возможность экспортировать **DataTable** или **DataView** непосредственно в файл Excel. Aspose.Words предлагает аналогичную функцию, которая позволяет разработчикам заполнять документ рассылки Word напрямую из любого .NET объекта данных. Каждый компонент в семействе Aspose предлагает свой собственный набор уникальных, мощных функций.

Лучшая часть покупки компонента Aspose или комплекта компонентов — это доступ к нашим командам разработчиков. Наши команды разработчиков понимают, что если вашей компании нужен определенный функционал, скорее всего, другим компаниям это тоже нужно. Хотя не все запросы на функционал могут быть реализованы, наши команды стараются быть очень открытыми и гибкими, предоставляя помощь. Такое мышление помогло компонентам Aspose стать такими мощными, какими они есть. Если вам нужны дополнительные функции от объектов автоматизации Office, ваши шансы на их добавление очень низки.

## **Заключение**

Эта статья охватывает ключевые моменты, почему компоненты Aspose являются лучшим выбором по сравнению с автоматизацией Office. Все различные компоненты Aspose предлагают версию для оценки без риска и без обязательств. Мы рекомендуем вам воспользоваться этой оценкой, чтобы увидеть, что Aspose может сделать для ваших приложений.

Для получения дополнительной информации смотрите следующие статьи в Интернете:

- [Топ 10 причин для разработчиков использовать .NET Framework 1.1](http://msdn2.microsoft.com/en-us/netframework/aa497339.aspx)
- [Рекомендации по серверной автоматизации Office](https://support.microsoft.com/?scid=kb;EN-US;q257757)[Лицензирование веб-компонентов Office 2000 и расширений Office Server](https://support.microsoft.com/?scid=kb;EN-US;q243006)
