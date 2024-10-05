---
title: "Переработка пула соединений"
url: /ru/java/connection-pool-refactored/
weight: 40
type: docs
---

С выходом Aspose.Email 19.3 пул соединений был переработан. Новый [EmailClient](https://apireference.aspose.com/email/java/com.aspose.email/EmailClient) класс был введен, который в конечном итоге заменит класс [CredentialsByHostClient](https://apireference.aspose.com/error/404?path=email/java/com.aspose.email/CredentialsByHostClient). Класс [EmailClient](https://apireference.aspose.com/email/java/com.aspose.email/EmailClient) предоставляет свойство [ConnectionAsgmtMode](https://apireference.aspose.com/email/java/com.aspose.email/EmailClient#getConnectionAsgmtMode\(\)), которое определяет режим распределения соединений в многопоточной среде. [EmailClient.ConnectionAsgmtMode](https://apireference.aspose.com/email/java/com.aspose.email/EmailClient#getConnectionAsgmtMode\(\)) устанавливается с помощью перечисления [ConnectionAsgmtType](https://apireference.aspose.com/email/java/com.aspose.email/ConnectionAsgmtType).
## **Типы соединений**
Существуют три типа соединений:

- Основное соединение: Это соединение создается и уничтожается вместе с почтовым клиентом. Оно не может быть созвано или уничтожено вручную.
- Установленное соединение: Пользователь может создать установленные соединения для потоков с помощью [`CreateConnection`](https://apireference.aspose.com/email/java/com.aspose.email/EmailClient#createConnection\(\)) метода. Если установленное соединение существует, все методы почтового клиента, выполняемые в потоке, будут неявно использовать это соединение. В каждом потоке может существовать только одно установленное соединение. Оно может быть создано вручную или автоматически. Это зависит от свойства `EmailClient.ConnectionAsgmtMode`. Эти соединения могут быть созданы вручную с помощью [`EmailClient.CreateConnection(createAsDefaultConnection = true)`](https://apireference.aspose.com/email/java/com.aspose.email/EmailClient#createConnection\(boolean\)) метода. Если установленное соединение не используется (в зависимости от режима распределения соединений), вместо него неявно используется основное соединение.
- Независимые соединения: Это соединения, которые не связаны с потоками. Их можно создавать вручную, и они должны использоваться явно в качестве параметра метода. Эти соединения могут быть созданы вручную с помощью [`EmailClient.CreateConnection()`](https://apireference.aspose.com/email/java/com.aspose.email/EmailClient#createConnection\(\)) метода или [`EmailClient.CreateConnection(createAsDefaultConnection = false`)](https://apireference.aspose.com/email/java/com.aspose.email/EmailClient#createConnection\(boolean\)) метода.
## **Типы распределения соединений**
Для установки свойства [EmailClient.ConnectionAsgmtMode](https://apireference.aspose.com/email/java/com.aspose.email/EmailClient#getConnectionAsgmtMode\(\)) используется перечисление [ConnectionAsgmtType](https://apireference.aspose.com/email/java/com.aspose.email/ConnectionAsgmtType). Типы распределения, предоставляемые [ConnectionAsgmtType](https://apireference.aspose.com/email/java/com.aspose.email/ConnectionAsgmtType), перечислены ниже.

- [`ConnectionAsgmtType.UseMainOrDefault`](https://apireference.aspose.com/email/java/com.aspose.email/ConnectionAsgmtType#UseMainOrDefault): Этот режим используется по умолчанию в почтовых клиентах. Почтовый клиент использует основное соединение для всех операций из нескольких потоков, если установленное соединение не было создано или если соединение не было передано явно в качестве параметра метода. Основное соединение — это соединение, которое создается одновременно с почтовым клиентом. Пользователь может создавать установленные соединения для потоков с помощью [`CreateConnection`](https://apireference.aspose.com/email/java/com.aspose.email/EmailClient#createConnection\(\)) метода. Если для потока создано установленное соединение, оно неявно используется для всех методов почтового клиента, которые вызываются в этом потоке. Если для потока не создано установленное соединение, основное соединение используется для всех методов почтового клиента, которые вызываются в этом потоке. Пользователь также может создавать соединения, не связанные с потоками (не установленные соединения) с помощью [`CreateConnection`](https://apireference.aspose.com/email/java/com.aspose.email/EmailClient#createConnection\(\)) метода. Если пользователь хочет использовать другие соединения (не основное и не установленное), он должен передать это соединение явно в качестве параметра метода, который он хочет использовать. Пользователь может дополнительно создавать любое количество соединений. Установленное соединение может быть только одно на поток. Обратите внимание, что установленные соединения работают корректно, если пользователь использует объекты Thread для многозадачного программирования. Если пользователь использует ConnectionPool или использует объекты Task для многозадачного программирования, этот режим может привести к неправильному поведению приложения. Чтобы избежать этой проблемы, пользователю необходимо вручную освободить установленное соединение (если он его использует) в конце выполнения кода.
- [`ConnectionAsgmtType.UseMain`](https://apireference.aspose.com/email/java/com.aspose.email/ConnectionAsgmtType#UseMain): Почтовый клиент использует основное соединение для всех операций из нескольких потоков. Основное соединение — это соединение, которое создается одновременно с почтовым клиентом. Пользователь не может создавать установленные соединения. Пользователь может создавать соединения, не связанные с потоками (не установленные соединения) с помощью [CreateConnection](https://apireference.aspose.com/email/java/com.aspose.email/EmailClient#createConnection\(\)) метода. Если пользователь хочет использовать другие соединения (не основное и не установленное), он должен передать это соединение явно в качестве параметра метода, который он хочет использовать.
- [`ConnectionAsgmtType.UseDefault`](https://apireference.aspose.com/email/java/com.aspose.email/ConnectionAsgmtType#UseDefault): Почтовый клиент неявно использует только установленные соединения для всех операций из нескольких потоков. Основное соединение в этом режиме не используется. Если для какого-то потока (первое вызов метода почтового клиента) не было создано установленное соединение, почтовый клиент автоматически создает установленное соединение для потока перед выполнением первой операции. Пользователь не может создавать установленные соединения для потоков с помощью [CreateConnection](https://apireference.aspose.com/email/java/com.aspose.email/EmailClient#createConnection\(\)) метода, потому что они создаются автоматически. Когда для потока создается установленное соединение, оно неявно используется для всех методов почтового клиента, которые вызываются в этом потоке. Пользователь также может создавать соединения, которые не связаны с потоками (не установленные соединения) с помощью [CreateConnection](https://apireference.aspose.com/email/java/com.aspose.email/EmailClient#createConnection\(\)) метода. Если пользователь хочет использовать другие соединения (не основное и не установленное), он должен передать это соединение явно в качестве параметра метода, который он хочет использовать. Пользователь может дополнительно создавать любое количество соединений. Только одно установленное соединение может использоваться на поток. Пожалуйста, обратите внимание, что установленные соединения работают корректно, если пользователь использует объекты Thread для многозадачного программирования. Если пользователь использует ConnectionPool или использует объекты Task для многозадачного программирования, этот режим может привести к неправильному поведению приложения. Чтобы избежать этой проблемы, пользователю необходимо вручную освободить установленное соединение в конце выполнения кода.