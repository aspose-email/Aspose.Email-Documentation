---
title: Work with Folders using Microsoft Graph
ArticleTitle: Work with Folders using Microsoft Graph
type: docs
weight: 20
url: /java/manage-folders-with-microsoft-graph/
---


**Aspose.Email for Java** allows you to perform a variety of folder operations in Microsoft Graph, such as listing, creating, updating, copying, moving, and deleting folders. Below are examples of common scenarios.


## **List Folders**

The following example retrieves all folders and prints their display names along with their properties:

~~~Java
GraphFolderInfoCollection folders = client.listFolders();
for (GraphFolderInfo folderInfo : folders) {
    System.out.println(folderInfo.getDisplayName());
    for (KeyValuePair<Long, MapiProperty> prop : folderInfo.getProperties()) {
        System.out.println(prop.getValue().getDescriptor().toString() + " " + prop.getValue().getString());
    }
}
~~~

## **List Subfolders from Inbox Folder**

You can also list subfolders under a specific folder, such as Inbox:


~~~Java
GraphFolderInfoCollection inboxFolders = client.listFolders(GraphKnownFolders.Inbox);
~~~


## **Create Folders**

You can create both root-level folders and subfolders.

### **Create a Root Folder**


~~~Java
GraphFolderInfo newFolder = client.createFolder("TEST_FOLDER");
~~~
### **Create Subfolders**

The following code sample shows how to create a subfolder under the Inbox folder:

~~~Java
GraphFolderInfo inboxTestSubFolder1 = client.createFolder(GraphKnownFolders.Inbox, "TEST_SUBFOLDER_1");
GraphFolderInfo inboxTestSubFolder2 = client.createFolder(newFolder.getItemId(), "TEST_SUBFOLDER_2");
~~~

## **Get Folder**

The following code sample demonstrates how to retrieve a specific folder, such as Sent Items:


~~~Java
GraphFolderInfo sentItemsFolder = client.getFolder(GraphKnownFolders.SentItems);
~~~

## **Update Folder**

You can update folder properties, for example, its display name:


~~~Java
GraphFolderInfo originalFolder = client.createFolder("TEST_FOLDER");
originalFolder.setDisplayName("NEW_TEST_FOLDER");
GraphFolderInfo updatedFolder = client.updateFolder(originalFolder);
~~~


## **Copy Folder and Its Content**

The following example shows how to copy a folder along with its subfolders and messages:


~~~Java
GraphFolderInfo parentFolder = client.createFolder("PARENT_FOLDER");
GraphFolderInfo testFolder = client.createFolder("TEST_FOLDER");
GraphFolderInfo testSubFolder = client.createFolder(testFolder.getItemId(), "TEST_SUBFOLDER");

MapiMessage message = new MapiMessage();
message.setSubject("Test subject");
message.setBody("Test body");
message.setProperty(KnownPropertyList.DISPLAY_TO, "to@host.com");
message.setProperty(KnownPropertyList.SENDER_NAME, "from");
message.setProperty(KnownPropertyList.SENT_REPRESENTING_EMAIL_ADDRESS, "from@host.com");
MapiMessage createdMessage = client.createMessage(testSubFolder.getItemId(), message);

GraphFolderInfo folderCopy = client.copyFolder(parentFolder.getItemId(), testFolder.getItemId());

GraphFolderInfoCollection folderColl = client.listFolders(parentFolder.getItemId());
// TEST_FOLDER
System.out.println(folderColl.get(0).getDisplayName());

folderColl = client.listFolders(folderColl.get(0).getItemId());
// TEST_SUBFOLDER
System.out.println(folderColl.get(0).getDisplayName());

GraphMessageInfoCollection listMessages = client.listMessages(folderColl.get(0).getItemId());
// Test subject
System.out.println(listMessages.get(0).getSubject());
~~~

## **Move Folder and Its Content**

You can also move a folder with all its content to another location:


~~~Java
GraphFolderInfo folder = client.moveFolder(parentFolder.getItemId(), testFolder.getItemId());
~~~


### **Delete Folder**

Use the following code sample to remove a folder permanently:

~~~Java
client.delete(testFolder.getItemId());
~~~

