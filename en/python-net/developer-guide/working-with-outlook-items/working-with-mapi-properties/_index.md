---
title: Working with MAPI Properties
type: docs
weight: 60
url: /python-net/working-with-mapi-properties/
---


## **Accessing and Setting Outlook MAPI Property**

The MapiProperty class represents a MAPI property, which contains:

- Name: a string that represents the property's name.
- Tag: a long that represents the property's tag.
- Data: a byte array which represents the property's data.

### **Getting MAPI Property using the MAPI Property Tag**

To get MAPI properties:

1. Create an instance of MapiMessage by loading from files or stream.
1. Get the MapiProperty from MapiMessage.Properties by MapiPropertyTag keys.
1. Get the Data of the MapiProperty by method GetX.

The following code snippet shows you how to get MAPI property using the MAPI property tag.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-GetMapiProperty-GetMapiProperty.py" >}}

### **Setting MAPI Properties**

The following code snippet shows you how to set MAPI properties.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-SetMapiProperties-SetMapiProperties.py" >}}



where the definition of convertDateTime method is as follow:



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ConvertDateTime-ConvertDateTime.py" >}}

## **Reading Named MAPI Properties from Outlook MSG Files**

Aspose.Email provides a set of APIs to work with MSG files, including the extraction of named MAPI properties.

### **Read Named MAPI Properties from MSG file**

To read named MAPI properties, we can use the **named_properties** property of the [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#mapimessage-class) class. The following code sample shows how to load a message, retrieve all named MAPI properties, iterate over each property to check its value:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")

# Get all named MAPI properties
properties = msg.named_properties.values
# Read all properties in foreach loop
for prop in properties:
    #  Read any specific property
    if prop.descriptor.canonical_name == "PidLidSideEffects":
        print(f"{prop.descriptor.canonical_name} = {prop}")
    if prop.descriptor.canonical_name == "PidLidInternetAccountName":
        print(f"{prop.descriptor.canonical_name} = {prop}")
```

## **Reading Named MAPI Property from Attachment**

Aspose.Email makes it possible to retrieve all named MAPI properties of an attachment. The following code sample shows how to read named MAPI properties from attachments:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")

# Get all named MAPI properties
attach_properties = msg.attachments[0].named_properties.values
# Read all properties in foreach loop
for prop in attach_properties:
    #  Read any specific property
    if prop.descriptor.name == "AttachmentOriginalUrl":
        print(f"{prop.descriptor.name} = {prop.get_string()}")
    if prop.descriptor.name == "AttachmentWasSavedToCloud":
        print(f"{prop.descriptor.name} = {prop.get_boolean()}")
```

## **Remove Properties from MSGs and Attachments**

This code sample demonstrates the creation of an Outlook MSG message with a body content and an attached message file. It also showcases how to delete an attachment property from the created message.

```python
import aspose.email as ae

# create an MSG
msg = ae.mapi.MapiMessage("from@doamin.com", "to@domain.com", "subject", "body");
msg.set_body_content("<html><body><h1>This is the body content</h1></body></html>", ae.mapi.BodyContentType.HTML)

# load message and add it to created MSG as attachment
attachment = ae.mapi.MapiMessage.load(attach.msg")
msg.attachments.add("Outlook2 Test subject.msg", attachment)

# count of attachment properties before removal
print(f"Before removal = {msg.attachments[0].properties.count}")

# Delete anyone attachment property
msg.attachments[0].remove_property(923467779)

# count of attachment properties after removal
print(f"Before removal = {msg.attachments[0].properties.count}")
```