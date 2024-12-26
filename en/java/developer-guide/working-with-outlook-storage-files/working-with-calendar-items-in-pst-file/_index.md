---
title: Working with Calendar Items in PST File
ArticleTitle: Working with Calendar Items in PST File
type: docs
weight: 50
url: /java/working-with-calendar-items-in-pst-file/
---

## **Adding MapiCalendar to PST**

[Create New PST, Add Sub-folders and Messages](/email/java/create-new-pst-add-sub-folders-and-messages/) showed how to create a PST file and add a subfolder to it. With Aspose.Email you can add [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) to the Calendar subfolder of a PST file that you have created or loaded.

Below are the steps to add [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) to a PST:

1. Create a [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) object.
1. Set the [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) properties using a constructor and methods.
1. Create a PST using the [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#create-java.lang.String-int-) method.
1. Create a pre-defined folder (Calendar) at the root of the PST file by accessing the root folder and then calling the [addMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/folderinfo/#addMapiMessageItem-com.aspose.email.IMapiMessageItem-) method.

The code snippet below shows how to create a [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) and then add it to the Calendar folder of a newly created PST file.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiCalendarToPST-.java" >}}

## **Save Calendar Items from Outlook PST to Disk in ICS format**

This article shows how to access calendar items from an Outlook PST file and save the calendar to disk in ICS format. It uses the [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) and [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) classes to get the calendar information.

Below are the steps to save the calendar items:

1. Load the PST file in the [PersonalStorage](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/) class.
1. Browse the Calendar folder.
1. Get the contents of the Calendar folder to get the message collection.
1. Loop through the message collection.
1. Call the [PersonalStorage.extractMessage()](https://reference.aspose.com/email/java/com.aspose.email/personalstorage/#extractMessage-com.aspose.email.MessageInfo-) method to get the contact information in the [MapiCalendar](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/) class.
1. Call the [MapiCalendar.save()](https://reference.aspose.com/email/java/com.aspose.email/mapicalendar/#save-java.io.OutputStream-) method to save the calendar item to disk in ICS format.

The program below loads a PST file from disk and saves all the calendar items in ICS format. The ICS files can then be used in any other program that can load the standard ICS calendar file. If you open any ICS file in Microsoft Outlook, it will look like the one in the below screenshot.

|![todo:image_alt_text](https://i.imgur.com/OhnGEXj.png)|
| :- |
|**Figure: Calendar item saved with Aspose.Email**|
{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-SaveCalendarItemsFromOutlookPSTToDiskInICSFormat-.java" >}}

## **Extract Calendar Items from a PST File**

MapiCalendar class represents a calendar item in the Microsoft Outlook MAPI format. Extract a message from a PST file and convert it into a MAPI message item. The following code sample extracts a calendar item from a PST file and converts it into a MapiCalendar object for further manipulation or processing:

```java
MapiCalendar cal = (MapiCalendar) pst.extractMessage(messageInfo).toMapiMessageItem();
```
## **Save Calendar Items in ICS format with Original Timestamp**

Use the above code sample to extract a calendar item from a PST file and then specify additional options to save it as ICS with original timestamp using the [setKeepOriginalDateTimeStamp](https://reference.aspose.com/email/java/com.aspose.email/mapicalendaricssaveoptions/#setKeepOriginalDateTimeStamp-boolean-) method of the [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/java/com.aspose.email/mapicalendaricssaveoptions/) class:

```java
MapiCalendar cal = (MapiCalendar) pst.extractMessage(messageInfo).toMapiMessageItem();

if (cal != null) {
    MapiCalendarIcsSaveOptions so = new MapiCalendarIcsSaveOptions();
    so.setKeepOriginalDateTimeStamp(true);
    cal.save("cal.ics", so);
}
```
## **Modify/Delete Occurrences from Recurrences**

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-ModifyDeleteOccurrencesFromRecurrence-ModifyDeleteOccurrencesFromRecurrence.java" >}}
