---
title: "Подключение к серверу Exchange"
url: /ru/cpp/connecting-to-exchange-server/
weight: 10
type: docs
---

Для подключения к серверам Exchange 2007, 2010 и 2013 с использованием Exchange Web Service класс Aspose.Email предоставляет [EWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client). Метод [GetEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.e_w_s_client#a1cba1af5a0bae889dedf76b9890ecb40) создает и возвращает объект [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client), который затем используется для выполнения операций, связанных с почтовым ящиком Exchange и другими папками. В этой статье показано, как создавать объекты [IEWSClient](https://apireference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client).

Следующий код показывает, как подключиться с помощью Exchange Web Service (EWS).



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-ConnectingToExchangeServerUsingEWS-ConnectingToExchangeServerUsingEWS.cpp" >}}