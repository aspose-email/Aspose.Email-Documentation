---
title: Filter Messages From Exchange Mailbox
ArticleTitle: Filter Messages From Exchange Mailbox
type: docs
weight: 30
url: /cpp/filter-messages-from-exchange-mailbox/
---

{{% alert color="primary" %}} 

Aspose.Email provides the capability to filter messages from Exchange Mailbox using the [EWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.e_w_s_client/) and ExchangeQueryBuilder. Messages can be filtered via different criteria such as by date, domain, messageId, and by Mail Delivery Notifications. This article shows how to filter messages from Exchange Server using different criteria.

{{% /alert %}} 
The [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/) class provides the [ListMessages()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#aad8420247acd17cb1d73303ed1982d1e) method which gets all messages from a mailbox. To get only messages which match some condition, use the overloaded [ListMessages()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#ac7bbdcc7ccacd4e8288ae6c7d929ea52) method which takes the *MailQuery* class as an argument. The *MailQuery* class provides various properties for specifying conditions, for example, date, subject, sender, and recipient.
##  **Filtering Messages**
To get filtered messages from a mailbox:

1. Connect to the Exchange server.
1. Create an instance of *MailQuery* and set the desired properties.
1. Call the [IEWSClient->ListMessages](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#ac7bbdcc7ccacd4e8288ae6c7d929ea52) method and pass the *MailQuery* in the parameters to get the filtered messages only.

The following code snippet shows you how to get messages that have the string "Newsletter" in the subject and were sent today.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesUsingEWS-FilterMessagesUsingEWS.cpp" >}}
##  **Filter Messages on Criteria**
The code samples above filters messages based on the email subject and date. We can filter on other properties too. Below are some examples of setting the conditions using *MailQuery*.
###  **Filter Criteria Today's Date**
The following code snippet shows you how to filter emails on the basis of today's date.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetEmailsWithTodayDate.cpp" >}}
###  **Filter Criteria Date Range**
The following code snippet shows you how to filter emails on the basis of a date range.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetEmailsOverDateRange.cpp" >}}
###  **Filter Criteria Specific Sender**
The following code snippet shows you how to filter emails on the basis of a specific sender.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificSenderEmails.cpp" >}}
###  **Filter Criteria Specific Domain**
The following code snippet shows you how to filter emails on the basis of a specific domain.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificDomainEmails.cpp" >}}
###  **Filter Criteria Specific Recipient**
The following code snippet shows you how to filter emails on the basis of a specific recipient.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificRecipientEmails.cpp" >}}
###  **Filter Criteria By MessageID**
The following code snippet shows you how to filter emails on the basis of MessageID.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificMessageIdEmail.cpp" >}}
###  **Filter Criteria All Mail Delivery Notifications**
The following code snippet shows you how to filter emails on the basis of all mail delivery notifications.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetMailDeliveryNotifications.cpp" >}}
###  **Filter by Message Size**
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-FilterMessagesByMessageSize.cpp" >}}
##  **Building Complex Queries**
If different [MailQueryBuilder](https://apireference.aspose.com/cpp/email/class/aspose.email.tools.search.mail_query_builder/) properties are set in a separate statement, all the conditions are matched. For example, to get a message in a particular date range and from a specific host, write three statements:
###  **Combining Queries with AND**
The following code snippet shows you how to Combine Queries with AND.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterWithComplexQueriesUsingEWS-CombineQueriesWithAND.cpp" >}}
###  **Combining Queries with OR**
[MailQueryBuilder](https://apireference.aspose.com/cpp/email/class/aspose.email.tools.search.mail_query_builder/) provides the [Or()](https://apireference.aspose.com/cpp/email/class/aspose.email.tools.search.mail_query_builder/#afc735b8cd80758418502678ac69eecd4) method which takes two *MailQuery* instances as parameters. It gets messages that match any of the two conditions specified. The example below filters messages that either has the word “test” in the subject or “noreply@host.com” as the sender. The following code snippet shows you how to combine queries with OR.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterWithComplexQueriesUsingEWS-CombiningQueriesWithOR.cpp" >}}
##  **Case-Sensitive Email Filtering**
Emails can be filtered based on case-sensitivity by specifying the IgnoreCase flag in the filter criteria as shown in the following code snippet.



{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CaseSensitiveEmailsFilteringUsingEWS-CaseSensitiveEmailsFiltering.cpp" >}}
#  **Filtering Messages with Paging Support**
{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-FilterMessagesWithPagingSupport.cpp" >}}
