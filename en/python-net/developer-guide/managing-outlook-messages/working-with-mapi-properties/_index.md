---
title: Working with MAPI Properties in Python
ArticleTitle: Working with MAPI Properties
type: docs
weight: 30
url: /python-net/working-with-mapi-properties-python/
---


## **Determine the MAPI Item Type in a PST Folder**

A PST file typically contains various types of data, such as email messages, calendar events, contacts, and more. The [MapiItemType](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiitemtype/) class of the Aspose.Email allows you to access and categorize different types of MAPI items within a PST file. The code below demonstrates how to determine the type of a MAPI item in a PST folder:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("test.pst")
folder = pst.root_folder.get_sub_folder("Calendar")
for messageInfo in folder.enumerate_messages():
    msg = pst.extract_message(messageInfo)

    # Get the class type based on msg.SupportedType
    item_type = msg.supported_type

    # Non-supported type. It cannot be accessed as appropriate item type.
    if item_type == ae.mapi.MapiItemType.NONE:
        print("Item type not supported")
    # An email message.
    elif item_type == ae.mapi.MapiItemType.MESSAGE:
        # You can access to MapiMessage properties there.
        # A subject for example
        print(msg.subject)
    # A contact item. Can be accessed as MapiContact.
    elif item_type == ae.mapi.MapiItemType.CONTACT:
        contact = msg.to_mapi_message_item()
        # You can access to MapiContact properties there. 
        # A name_info.display_name for example. 
        print(contact.name_info.display_name)
    # A calendar item. Can be accessed as MapiCalendar.
    elif item_type == ae.mapi.MapiItemType.CALENDAR:
        calendar = msg.to_mapi_message_item()
        # You can access to MapiCalendar properties there. 
        # A location for example. 
        print(calendar.location)
    # A distribution list. Can be accessed as MapiDistributionList.
    elif item_type == ae.mapi.MapiItemType.DIST_LIST:
        dlist = msg.to_mapi_message_item()
        # You can access to MapiDistributionList properties there
    # A Journal entry. Can be accessed as MapiJournal.
    elif item_type == ae.mapi.MapiItemType.JOURNAL:
        journal = msg.to_mapi_message_item()
        # You can access to MapiJournal properties there
    # A StickyNote. Can be accessed as MapiNote.
    elif item_type == ae.mapi.MapiItemType.NOTE:
        note = msg.to_mapi_message_item()
        # You can access to MapiNote properties there
    # A Task item. Can be accessed as MapiTask.
    elif item_type == ae.mapi.MapiItemType.TASK:
        task = msg.to_mapi_message_item()
        # You can access to MapiTask properties there

```

## **Access and Manage MAPI Properties**

The [MapiProperty](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapiproperty/) class represents a MAPI property, which contains:

- Name: a string that represents the property's name.
- Tag: a long integer that represents the property's tag.
- Data: a byte array which represents the property's data.

### **Get MAPI Property Using Property Tag**

The code sample below loads a MAPI message, retrieves key properties like the subject and internet code page, and safely handles the potential absence of these properties. To get MAPI properties:

1. Load the MAPI message from a file using the [load](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#methods) method.
2. Use the [MapiPropertyTag](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapipropertytag/) class to access specific properties from a MAPI message, such as the subject and internet code page.
3. Handle missing properties.

```py
# Load from file
msg = MapiMessage.load(dataDir + "message.msg")

# Access the MapiPropertyTag.PR_SUBJECT property
prop = msg.properties[MapiPropertyTag.SUBJECT]

# If the property is not found, check the MapiPropertyTag.PR_SUBJECT_W (which is a // Unicode peer of the MapiPropertyTag.PR_SUBJECT)
if prop is None:
	prop = msg.properties[MapiPropertyTag.SUBJECT_W]

# Cannot found
if prop is None:
	print("No property found!")

# Get the property data as string
subject = prop.get_string()

print("Subject:" + subject)

# Read internet code page property
prop = msg.properties[MapiPropertyTag.INTERNET_CPID]
if prop is not None:
	print("CodePage:" + str(prop.get_long()))
```

### **Set MAPI Properties**

The following code snippet shows you how to set MAPI properties.


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-SetMapiProperties-SetMapiProperties.py" >}}


## **Read Named MAPI Properties**

Aspose.Email provides a set of APIs to work with MSG files, including the extraction of named MAPI properties.

### **Read Named MAPI Properties from MSG Files**

To read named MAPI properties, you can use the [named_properties](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#properties) property of the [MapiMessage](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#mapimessage-class) class. The following code sample shows how to load a message, retrieve all named MAPI properties, iterate over each property to check its value:

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

## **Read Named MAPI Properties from Attachments**

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

## **Property Management**

### **Remove Properties from MSG Files and Attachments**

This code sample below demonstrates the creation of an Outlook MSG message with a body content and an attached message file. It also showcases how to delete an attachment property from the created message.

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

## **Converting MSG to MIME Message**

Aspose.Email API provides the capability of converting MSG file to MIME message using the [to_mail_message](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapimessage/#methods) method.


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-ConvertMSGToMimeMessage-ConvertMSGToMimeMessage.py" >}}

## **Setting Timeout for Message Conversion and Loading**

To limit the time in milliseconds of the message conversion (default value 3 sec), the **timeout** property of the [MailConversionOptions](https://reference.aspose.com/email/python-net/aspose.email.mapi/mailconversionoptions/#mailconversionoptions-class) class is used. 

Here's how you can set a timeout for message conversion and loading processes:

```py
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")
options = ae.mapi.MailConversionOptions()
options.timeout = 5000
mailMessage = msg.to_mail_message(options)
```

By setting a timeout for message conversion and loading processes, you can control the maximum time these operations are allowed to run. After setting the timeout, you can proceed with your message conversion and loading processes. 


## **Set Color Category for Outlook MSG Files**

Sometimes you may need to differentiate emails of particular importance and visually organize them. The library provides a way to do this by assigning a specific color to a message item. When you set a color category for an item, it allows you to easily identify and locate related items at a glance. Use [FollowUpManager](https://reference.aspose.com/email/python-net/aspose.email.mapi/followupmanager/#followupmanager-class) class to set the color category for a message as shown in the following code example:

```python
import aspose.email as ae

msg = ae.mapi.MapiMessage.load("my.msg")

# Add Two categories
ae.mapi.FollowUpManager.add_category(msg, "Purple Category")
ae.mapi.FollowUpManager.add_category(msg, "Red Category")

# Retrieve the list of available categories
categories = ae.mapi.FollowUpManager.get_categories(msg)

# Remove the specified category and then Clear all categories
ae.mapi.FollowUpManager.remove_category(msg, "Red Category")
ae.mapi.FollowUpManager.clear_categories(msg)
```
