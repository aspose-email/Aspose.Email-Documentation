---
title: "Подключение к серверу Exchange"
url: /ru/cpp/connecting-to-exchange-server/
weight: 10
type: docs
---

Чтобы подключиться к серверам Exchange 2007, 2010 и 2013 с помощью веб-службы Exchange, Aspose.Email предоставляет [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client) класс. [GetEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client#a1cba1af5a0bae889dedf76b9890ecb40) метод создает экземпляр и возвращает [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client) объект, который в дальнейшем используется для выполнения операций, связанных с почтовым ящиком Exchange и другими папками. В этой статье показано, как создавать экземпляры объектов [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).

В следующем фрагменте кода показано, как подключиться с помощью веб-службы Exchange (EWS).



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ConnectingToExchangeServerUsingEWS-ConnectingToExchangeServerUsingEWS.cpp" >}}
