---
title: Working with Calendar Items in PST File
type: docs
weight: 50
url: /net/working-with-calendar-items-in-pst-file/
---


## **Adding MapiCalendar to PST**

[Create a New PST File and Add Subfolders](https://docs.aspose.com/email/net/create-new-pst-add-sub-folders-and-messages/#creating-a-new-pst-file-and-add-subfolders) showed how to create a PST file and add a subfolder to it. With Aspose.Email you can add MapiCalendar to the Calendar subfolder of a PST file that you have created or loaded. Below are the steps to add MapiCalendar to a PST:

1. Create a [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/) object.
2. Set the [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/) properties using a constructor and methods.
3. Create a PST using the [PersonalStorage.Create()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create/) method.
4. Create a pre-defined folder (Calendar) at the root of the PST file by accessing the root folder and then calling the [AddMapiMessageItem()](https://reference.aspose.com/email/net/aspose.email.storage.pst/folderinfo/addmapimessageitem/#addmapimessageitem) method.

The following code snippet shows you how to create a [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/) and then add it to the calendar folder of a newly created PST file.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-AddMapiCalendarToPST-AddMapiCalendarToPST.cs" >}}

## **Save Calendar Items from PST to Disk in ICS Format**

This article shows how to access calendar items from an Outlook PST file and save the calendar to disk in ICS format. Use the [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) and [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/) classes to get the calendar information. Below are the steps to save calendar items :

1. Load the PST file in the [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) class.
1. Browse the Calendar folder.
1. Get the contents of the Calendar folder to get the message collection.
1. Loop through the message collection.
1. Call [PersonalStorage.ExtractMessage()](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/extractmessage/#extractmessage/) method to get the contact information in the [MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/) class.
1. Call the [MapiCalendar.Save()](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/save/#save/) method to save the calendar item to disk in ICS format.

The program below loads a PST file from disk and saves all the calendar items in ICS format. The ICS files can then be used in any other program that can load the standard ICS calendar file. Opened in Microsoft Outlook, an ICS file looks like the one in the below screenshot.

|![todo:image_alt_text](working-with-calendar-items-in-pst-file_1.png)|
| :- |
The following code snippet shows you how to export the calendar items from Outlook PST to ICS format.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SaveCalendarItems-SaveCalendarItems.cs" >}}

### **Saving as ICS with Original Timestamp**

The following features are available to save calendar items as ICS preserving their original date and time information:

- [MapiCalendarIcsSaveOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/) - Allows to specify additional options when saving MapiCalendar to Ics format. 

- [MapiCalendarIcsSaveOptions.KeepOriginalDateTimeStamp](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendaricssaveoptions/keeporiginaldatetimestamp/) - Allows keep original DateTimeStamp value in output file.

Use the code sample below to implement the features to your project:

```cs
var cal = pst.ExtractMessage(msgInfo).ToMapiMessageItem() as MapiCalendar;

if (cal != null)
{
  cal.Save("cal.ics", new MapiCalendarIcsSaveOptions() { KeepOriginalDateTimeStamp = true});
}
```

## **Modify/Delete Occurrences from Recurrences**

Exceptions can be added to existing recurrences using Aspose.Email for .NET API. The following code sample illustrates the usage of this feature.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ModifyDeleteOccurrenceInRecurrence-ModifyDeleteOccurrenceInRecurrence.cs" >}}
