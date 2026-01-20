---
title: Creating Forward and Reply Messages with Aspose.Email
ArticleTitle: Creating Forward and Reply Messages
type: docs
weight: 40
url: /python-net/create-forward-and-reply-messages-in-python/
---


## **Create a Forward Message**

Aspose.Email provides straightforward ways to create forward and reply messages based on the existing ones. You can use the [ForwardMessageBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools/forwardmessagebuilder/#forwardmessagebuilder-class) class to create a forward message by setting the source message, sender, recipients, subject, and body. Forward messages can include the original message as an attachment or as the body of the forwarded message. You have the flexibility to customize additional properties such as attachments, headers, and formatting options. The code sample below shows how to create a forward message:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("original.msg")

builder = ae.tools.ForwardMessageBuilder()
builder.addition_mode = ae.tools.OriginalMessageAdditionMode.TEXTPART

forwardMsg = builder.build_response(msg)
forwardMsg.save("forward_out.msg")
```

## **Create a Reply Message**

The [ReplyMessageBuilder](https://reference.aspose.com/email/python-net/aspose.email.tools/replymessagebuilder/#replymessagebuilder-class) class is used to configure reply settings, including the source message, sender, recipients, reply mode, subject prefix, and the reply message body. Reply messages can be created in different reply modes like "Reply to Sender" or "Reply to All" based on your requirement. You can customize various properties such as attachments, headers, and formatting options for the reply message. The code sample below shows how to create a forward message:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("original.msg")

builder = ae.tools.ReplyMessageBuilder()

# Set ReplyMessageBuilder Properties
builder.reply_all = True
builder.addition_mode = ae.tools.OriginalMessageAdditionMode.TEXTPART
builder.response_text = "<p><b>Dear Friend,</b></p> I want to do is introduce my co-author and co-teacher. <p><a href=\"www.google.com\">This is a first link</a></p><p><a href=\"www.google.com\">This is a second link</a></p>";

replyMsg = builder.build_response(msg)
replyMsg.save("reply_out.msg")
```
