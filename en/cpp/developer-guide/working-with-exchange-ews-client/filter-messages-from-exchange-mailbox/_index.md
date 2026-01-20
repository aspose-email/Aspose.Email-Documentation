---
title: Filter Messages From Exchange Mailbox
ArticleTitle: Filter Messages From Exchange Mailbox
type: docs
weight: 30
url: /cpp/filter-messages-from-exchange-mailbox/
description: Learn how to filter Exchange mailbox messages by date, sender, domain, MessageID, and more using IEWSClient and ExchangeQueryBuilder in C++.
---


**Aspose.Email for C++** allows developers to filter messages in an Exchange mailbox using [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/), [MailQuery](https://reference.aspose.com/email/cpp/class/aspose.email.tools.search.mail_query/), and [ExchangeQueryBuilder](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_query_builder/). You can filter messages by date, sender, domain, MessageID, delivery notifications, and many other criteria.

To retrieve messages from a folder for further processing, the [IEWSClient.](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/) has the following methods:

- [ListMessages()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#aad8420247acd17cb1d73303ed1982d1e) - Gets all messages from a mailbox.  
- [ListMessages()](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#ac7bbdcc7ccacd4e8288ae6c7d929ea52) overload - Returns only messages that match specific conditions. It accepts a [MailQuery](https://reference.aspose.com/email/cpp/class/aspose.email.tools.search.mail_query/) which defines filtering rules such as subject keywords, date ranges, and address-based filtering.


##  **Filter Messages with IEWSClient**

The following code sample demonstrates how to query and retrieve specific emails from an Exchange Server using Exchange Web Services (EWS) with Aspose.Email for C++. It shows the complete process of connecting to an Exchange server (Office 365 in this case), building a search query to find messages with "Newsletter" in the subject that arrived today, executing the query against the inbox, retrieving the matching messages, and properly handling the connection lifecycle with error handling.

1. Connect to the Exchange server using [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/).
2. Create a [MailQuery](https://reference.aspose.com/email/cpp/class/aspose.email.tools.search.mail_query/) or [ExchangeQueryBuilder](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_query_builder/) and define filtering conditions.
3. Call [ListMessages(folderUri, query)](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/#ac7bbdcc7ccacd4e8288ae6c7d929ea52) to get the filtered results.


{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesUsingEWS-FilterMessagesUsingEWS.cpp" >}}


##  **Filter Messages on Criteria**

The code sample above filters messages based on the email subject and date. You can filter on other properties too. Below are some examples of setting the conditions using [MailQuery](https://reference.aspose.com/email/cpp/class/aspose.email.tools.search.mail_query/).

###  **Filter by Today's Date**

The following code sample demonstrates how to build a query to find emails that arrived today.


{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetEmailsWithTodayDate.cpp" >}}

###  **Filter by Date Range**

The following code sample demonstrates how to build a query to find emails that arrived within the last 7 days.


{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetEmailsOverDateRange.cpp" >}}

###  **Filter by Specific Sender**


The following code sample demonstrates how to build a query to find emails from a specific sender.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificSenderEmails.cpp" >}}

###  **Filter by Domain**


The following code sample demonstrates how to build a query to find emails from a specific domain.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificDomainEmails.cpp" >}}

###  **Filter by Recipient**


The following code sample demonstrates how to build a query to find emails sent to a specific recipient.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificRecipientEmails.cpp" >}}

###  **Filter by MessageID**

The following code sample demonstrates how to build a query to find a specific email by its MessageId.


{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetSpecificMessageIdEmail.cpp" >}}

###  **Filter Mail Delivery Notifications**


The following code sample demonstrates how to build a query to find Mail Delivery Notifications (MDNs).

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-GetMailDeliveryNotifications.cpp" >}}

###  **Filter by Message Size**

The following code sample demonstrates how to build a query to find emails larger than a specific size.

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-FilterMessagesByMessageSize.cpp" >}}

##  **Build Complex Queries**

When using [MailQueryBuilder](https://apireference.aspose.com/cpp/email/class/aspose.email.tools.search.mail_query_builder/) or [ExchangeQueryBuilder](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.exchange_query_builder/), each property you set creates a filtering condition. If these conditions are defined in separate statements, they are combined using logical AND, meaning all conditions must match for a message to be returned.

This allows developers to build precise filters such as:

- Emails within a date range
- Emails from a specific domain
- Emails matching multiple criteria simultaneously


###  **Combine Queries with AND**

Using multiple builder properties in sequence automatically creates an **AND** operation.

The following example retrieves messages that:

- Come from a specific domain
- Arrived before today
- Arrived within the last seven days

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterWithComplexQueriesUsingEWS-CombineQueriesWithAND.cpp" >}}


###  **Combine Queries with OR**

To match messages that satisfy either of two conditions, use the **Or()** method.

The following example gets messages that:

- Contain “test” in the subject, **or**
- Were sent by “noreply@host.com”


{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterWithComplexQueriesUsingEWS-CombiningQueriesWithOR.cpp" >}}


##  **Case-Sensitive Email Filtering**


You can apply case-sensitive or case-insensitive filtering when querying messages from an Exchange mailbox. To control this behavior, use the IgnoreCase flag available in the filtering methods. Passing true enables case-insensitive matching.

The example below filters messages that:

- Contain the word "Newsletter" in the subject (case-insensitive)
- Arrived today

{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-CaseSensitiveEmailsFilteringUsingEWS-CaseSensitiveEmailsFiltering.cpp" >}}


##  **Pagination in Message Filtering**

When working with large Exchange mailboxes, paging allows you to retrieve messages in smaller, manageable batches. The [ListMessagesByPage](https://reference.aspose.com/email/cpp/class/aspose.email.clients.exchange.web_service.i_e_w_s_client#a50ea10548ed8e1b305bdeb322b8c109f) method of [IEWSClient](https://apireference.aspose.com/cpp/email/class/aspose.email.clients.exchange.web_service.i_e_w_s_client/) returns results page-by-page based on a specified page size and query criteria.

The example below demonstrates how to:

1. Build a filter using [MailQueryBuilder](https://apireference.aspose.com/cpp/email/class/aspose.email.tools.search.mail_query_builder/).
2. Retrieve results in pages.
3. Loop through all pages until the last one.
4. Count the total number of matching messages.


{{< gist "aspose-com-gists" "525dd06c8783ebb18fb75cfc4b31d1ef" "Examples-Cpp-source-Exchange_EWS-FilterMessagesOnCriteriaUsingEWS-FilterMessagesWithPagingSupport.cpp" >}}
