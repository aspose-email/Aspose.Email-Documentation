---
title: How to use GraphClient for Microsoft Graph
type: docs
weight: 20
url: /net/how-to-use-graphclient-for-microsoft-graph/
---


## **Working with GraphClient**
Microsoft Graph 
The implementation of Graph Client in Aspose.Email for .NET, allows to access Microsoft Graph from our API.
In the examples below we will create an instance of MS Graph Client, providing the token into it. 
Then, we will examine the main methods to manage folders, update them, copy and delete. Messages, their content and 
attachments can also be accessed or changed with our MS Graph Client. Managing categories, rules, notebooks and overrides is an 
extended feature of Microsoft Graph Client by Aspose.Email, which you will learn with ease. 


### **Create GraphClient Object**
Create [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient) object to make requests against the service.
After you have a [IGraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient) that is authenticated, you can begin making calls against the service.

~~~csharp
IGraphClient client = GraphClient.GetClient(tokenProvider);
~~~


## **Manage Folders**
### **List Folders**
By calling [ListFolders](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/methods/listfolders) 
method from Ms Graph Client, its possible to get the list of folders. Each folder has a set of parameters like 
DisplayName, which can be read in [FolderInfo](https://reference.aspose.com/email/net/aspose.email.clients.activesync.transportlayer/folderinfo) type.

~~~csharp
            using (IGraphClient client = TestUtil.CreateGraphClient(user))
            {
                FolderInfoCollection folders = client.ListFolders();
                bool containsInbox = false;
                foreach (FolderInfo folderInfo in folders)
                    if ("Inbox".Equals(folderInfo.DisplayName, StringComparison.InvariantCultureIgnoreCase))
                    {
                        containsInbox = true;
                        break;
                    }
            }
~~~
### **Update Folder**
To create folder with Ms Graph Client, use [CreateFolder](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/methods/createfolder) 
method. You will get [FolderInfo](https://reference.aspose.com/email/net/aspose.email.clients.activesync.transportlayer/folderinfo) object 
and the possibility to access DisplayName, ItemId, HasSubFolders and other properties.

~~~csharp
            using (IGraphClient client = TestUtil.CreateGraphClient(user))
            {
                FolderInfo folderInfo = null;
                try
                {
                    string name = "EMAILNET_39343_" + Guid.NewGuid().ToString();
                    folderInfo = client.CreateFolder(name);
                    folderInfo.DisplayName = "EMAILNET_39343_" + Guid.NewGuid().ToString();
                    FolderInfo folderInfo2 = client.UpdateFolder(folderInfo);
                }
                finally
                {
                    if (folderInfo != null)
                        client.Delete(folderInfo.ItemId);
                }
            }
~~~

### **Copy Folder**
[CopyFolder](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/methods/copyfolder) method is the key method to copy the folder object 
with MS Graph.

~~~csharp
            using (IGraphClient client = TestUtil.CreateGraphClient(user))
            {
                FolderInfoCollection folderInfoCol = client.ListFolders();
                foreach (FolderInfo folderInfo in folderInfoCol)
                    if (folderInfo.DisplayName.StartsWith("EMAILNET", StringComparison.InvariantCultureIgnoreCase))
                        client.Delete(folderInfo.ItemId);
                string baseName = "EMAILNET-39345";
                try
                {
                    folderInfoCol = client.ListFolders();
                    foreach (FolderInfo folderInfo in folderInfoCol)
                        if (folderInfo.DisplayName.StartsWith("EMAILNET", StringComparison.InvariantCultureIgnoreCase))
                            client.Delete(folderInfo.ItemId);
                    FolderInfo folder_1 = client.CreateFolder(baseName + "_1_" + Guid.NewGuid().ToString());
                    FolderInfo folder_2 = client.CreateFolder(baseName + "_2_" + Guid.NewGuid().ToString());
                    folderInfoCol = client.ListFolders();
                    FolderInfo folder_1_1 = client.CreateFolder(folder_1.ItemId, baseName + "_1_1_" + Guid.NewGuid().ToString());
                    FolderInfo folder_1_2 = client.CreateFolder(folder_1.ItemId, baseName + "_1_2_" + Guid.NewGuid().ToString());
                    folderInfoCol = client.ListFolders();
                    FolderInfo newFolder = client.CopyFolder(folder_2.ItemId, folder_1.ItemId);
                    FolderInfoCollection folderInfoCol1 = client.ListFolders();
                    FolderInfoCollection folderInfoCol2 = client.ListFolders(folder_2.ItemId);
                    bool folder1Exists = false;
                    foreach (FolderInfo folderInfo in folderInfoCol1)
                        if (folderInfo.DisplayName == folder_1.DisplayName)
                            folder1Exists = true;
                    folder1Exists = false;
                    foreach (FolderInfo folderInfo in folderInfoCol2)
                        if (folderInfo.DisplayName == folder_1.DisplayName)
                            folder1Exists = true;
                    bool folder11Exists = false;
                    bool folder12Exists = false;
                    FolderInfoCollection folderInfoCol3 = client.ListFolders(newFolder.ItemId);
                    foreach (FolderInfo folderInfo in folderInfoCol3)
                    {
                        if (folderInfo.DisplayName.Equals(folder_1_1.DisplayName, StringComparison.InvariantCultureIgnoreCase))
                            folder11Exists = true;
                        if (folderInfo.DisplayName.Equals(folder_1_2.DisplayName, StringComparison.InvariantCultureIgnoreCase))
                            folder12Exists = true;
                    }
                }
                finally
                {
                    folderInfoCol = client.ListFolders();
                    foreach (FolderInfo folderInfo in folderInfoCol)
                        if (folderInfo.DisplayName.StartsWith("EMAILNET", StringComparison.InvariantCultureIgnoreCase))
                            client.Delete(folderInfo.ItemId);
                }
            }
~~~
### **Move and Delete Folder**
Use [MoveFolder](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/methods/movefolder) method is 
used to move the folder, it accepts newParentId and itemId. [Delete](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/methods/delete) 
method is used to delete method by id.

~~~csharp
            using (IGraphClient client = TestUtil.CreateGraphClient(user))
            {
                FolderInfoCollection folderInfoCol = client.ListFolders();
                foreach (FolderInfo folderInfo in folderInfoCol)
                    if (folderInfo.DisplayName.StartsWith("EMAILNET", StringComparison.InvariantCultureIgnoreCase))
                        client.Delete(folderInfo.ItemId);
                string baseName = "EMAILNET-39345";
                try
                {
                    folderInfoCol = client.ListFolders();
                    foreach (FolderInfo folderInfo in folderInfoCol)
                        if (folderInfo.DisplayName.StartsWith("EMAILNET", StringComparison.InvariantCultureIgnoreCase))
                            client.Delete(folderInfo.ItemId);
                    FolderInfo folder_1 = client.CreateFolder(baseName + "_1_" + Guid.NewGuid().ToString());
                    FolderInfo folder_2 = client.CreateFolder(baseName + "_2_" + Guid.NewGuid().ToString());
                    folderInfoCol = client.ListFolders();
                    FolderInfo folder_1_1 = client.CreateFolder(folder_1.ItemId, baseName + "_1_1_" + Guid.NewGuid().ToString());
                    FolderInfo folder_1_2 = client.CreateFolder(folder_1.ItemId, baseName + "_1_2_" + Guid.NewGuid().ToString());
                    folderInfoCol = client.ListFolders();
                    FolderInfo newFolder = client.MoveFolder(folder_2.ItemId, folder_1.ItemId);
                    FolderInfoCollection folderInfoCol1 = client.ListFolders();
                    FolderInfoCollection folderInfoCol2 = client.ListFolders(folder_2.ItemId);
                    bool folder1Exists = false;
                    foreach (FolderInfo folderInfo in folderInfoCol1)
                        if (folderInfo.DisplayName == folder_1.DisplayName)
                            folder1Exists = true;
                    folder1Exists = false;
                    foreach (FolderInfo folderInfo in folderInfoCol2)
                        if (folderInfo.DisplayName == folder_1.DisplayName)
                            folder1Exists = true;
                    bool folder11Exists = false;
                    bool folder12Exists = false;
                    FolderInfoCollection folderInfoCol3 = client.ListFolders(newFolder.ItemId);
                    foreach (FolderInfo folderInfo in folderInfoCol3)
                    {
                        if (folderInfo.DisplayName.Equals(folder_1_1.DisplayName, StringComparison.InvariantCultureIgnoreCase))
                            folder11Exists = true;
                        if (folderInfo.DisplayName.Equals(folder_1_2.DisplayName, StringComparison.InvariantCultureIgnoreCase))
                            folder12Exists = true;
                    }
                }
                finally
                {
                    folderInfoCol = client.ListFolders();
                    foreach (FolderInfo folderInfo in folderInfoCol)
                        if (folderInfo.DisplayName.StartsWith("EMAILNET", StringComparison.InvariantCultureIgnoreCase))
                            client.Delete(folderInfo.ItemId);
                }
            }
~~~

## **Manage Messages**
MS Graph Client, implemented in Aspose.Email for .NET provides a set of methos to manage messages and attachments:
* [List](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/methods/listmessages) messages
* [Fetch](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/methods/fetchmessage) message
* [Create](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/methods/createmessage) message
* [Send](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/methods/send) message
* [CopyMessage](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/methods/copymessage) message
* [Move](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/methods/movemessage) message
* [CreateAttachment](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/methods/createattachment)
* [FetchAttachment](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/methods/fetchattachment)
* [DeleteAttachment](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/methods/deleteattachment)
* [ListAttachments](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/methods/listattachments)


### **List Messages**


~~~csharp
            using (IGraphClient client = TestUtil.CreateGraphClient(user))
            {
                FolderInfoCollection folderInfoCol1 = client.ListFolders();
                FolderInfo inbox = null;
                foreach (FolderInfo folderInfo in folderInfoCol1)
                {
                    if (folderInfo.DisplayName.Equals("Inbox", StringComparison.InvariantCultureIgnoreCase))
                    {
                        inbox = folderInfo;
                        break;
                    }
                }
                MessageInfoCollection messageInfoCol = client.ListMessages(inbox.ItemId);

            }
~~~
### **Fetch Message**


~~~csharp
            using (IGraphClient client = TestUtil.CreateGraphClient(user))
            {
                FolderInfoCollection folderInfoCol1 = client.ListFolders();
                FolderInfo inbox = null;
                foreach (FolderInfo folderInfo in folderInfoCol1)
                {
                    if (folderInfo.DisplayName.Equals("Inbox", StringComparison.InvariantCultureIgnoreCase))
                    {
                        inbox = folderInfo;
                        break;
                    }
                }
                MessageInfoCollection messageInfoCol = client.ListMessages(inbox.ItemId);
                MessageInfo messageInfo = messageInfoCol[0];
                MapiMessage message = client.FetchMessage(messageInfo.ItemId);
            }
~~~
### **Create Message**

~~~csharp
            using (IGraphClient client = TestUtil.CreateGraphClient(user))
            {
                MapiMessage mm = new MapiMessage();
                mm.Subject = "EMAILNET-39318 " + Guid.NewGuid().ToString();
                mm.Body = "EMAILNET-39318 REST API v1.0 - Create Message";
                mm.SetProperty(KnownPropertyList.DisplayTo, user.EMail);
                int offset = 0;
                MailAddress address = MailBnfHelper.ReadMailAddress(user.EMail, ref offset, true);                
                mm.SetProperty(KnownPropertyList.SenderName, address.DisplayName);
                mm.SetProperty(KnownPropertyList.SentRepresentingEmailAddress, address.Address);
                MapiMessage createdMessage = client.CreateMessage(KnownFolders.Inbox, mm);
                MapiProperty objectUri = createdMessage.GetProperty(KnownPropertyList.ObjectUri);
                string uri = objectUri.GetString();
                MapiMessage fetchedMessage = client.FetchMessage(uri);
                fetchedMessage.Subject = "EMAILNET-39320 REST API v1.0 - Update message";
                MapiMessage updatedMessage = client.UpdateMessage(fetchedMessage);
                client.Delete(uri);
            }
~~~
### **Send Message**


~~~csharp
            using (IGraphClient client = TestUtil.CreateGraphClient(user))
            {
                try
                {
                    MapiMessage mm = new MapiMessage();
                    mm.Subject = "EMAILNET-39329 " + Guid.NewGuid().ToString();
                    mm.Body = "EMAILNET-39329 REST API v1.0 - Send a message";
                    mm.SetProperty(KnownPropertyList.DisplayTo, user.EMail);
                    int offset = 0;
                    MailAddress address = MailBnfHelper.ReadMailAddress(user.EMail, ref offset, true);
                    mm.SetProperty(KnownPropertyList.SenderName, address.DisplayName);
                    mm.SetProperty(KnownPropertyList.SentRepresentingEmailAddress, address.Address);
                    client.Send(mm);
                }
                finally
                {
                }
~~~
### **Send Draft Message**


~~~csharp
            using (IGraphClient client = TestUtil.CreateGraphClient(user))
            {
                try
                {
                    MapiMessage mm = new MapiMessage();
                    mm.Subject = "EMAILNET-39322 " + Guid.NewGuid().ToString();
                    mm.Body = "EMAILNET-39322 REST API v1.0 - Send draft";
                    mm.SetProperty(KnownPropertyList.DisplayTo, user.EMail);
                    int offset = 0;
                    MailAddress address = MailBnfHelper.ReadMailAddress(user.EMail, ref offset, true);
                    mm.SetProperty(KnownPropertyList.SenderName, address.DisplayName);
                    mm.SetProperty(KnownPropertyList.SentRepresentingEmailAddress, address.Address);
                    MapiMessage draftMessage = client.CreateMessage(KnownFolders.Drafts, mm);
                    client.Send(draftMessage.ItemId);
                }
                finally
                {
                }
~~~
### **Copy Message**


~~~csharp
            using (IGraphClient client = TestUtil.CreateGraphClient(user))
            {
                try
                {
                    MapiMessage mm = new MapiMessage();
                    mm.Subject = "EMAILNET-39323 " + Guid.NewGuid().ToString();
                    mm.Body = "EMAILNET-39323 REST API v1.0 - Copy messages";
                    mm.SetProperty(KnownPropertyList.DisplayTo, user.EMail);
                    int offset = 0;
                    MailAddress address = MailBnfHelper.ReadMailAddress(user.EMail, ref offset, true);
                    mm.SetProperty(KnownPropertyList.SenderName, address.DisplayName);
                    mm.SetProperty(KnownPropertyList.SentRepresentingEmailAddress, address.Address);
                    MapiMessage draftMessage = client.CreateMessage(KnownFolders.Drafts, mm);
                    MapiMessage copiedMessage = client.CopyMessage(KnownFolders.Inbox, draftMessage.ItemId);
                    MapiMessage fetchedMessage = client.FetchMessage(copiedMessage.ItemId);
                }
                finally
                {
                }
~~~
### **Move Message**


~~~csharp
            using (IGraphClient client = TestUtil.CreateGraphClient(user))
            {
                try
                {
                    MapiMessage mm = new MapiMessage();
                    mm.Subject = "EMAILNET-39324 " + Guid.NewGuid().ToString();
                    mm.Body = "EMAILNET-39324 REST API v1.0 - Move messages";
                    mm.SetProperty(KnownPropertyList.DisplayTo, user.EMail);
                    int offset = 0;
                    MailAddress address = MailBnfHelper.ReadMailAddress(user.EMail, ref offset, true);
                    mm.SetProperty(KnownPropertyList.SenderName, address.DisplayName);
                    mm.SetProperty(KnownPropertyList.SentRepresentingEmailAddress, address.Address);
                    MapiMessage draftMessage = client.CreateMessage(KnownFolders.Drafts, mm);
                    MapiMessage movedMessage = client.MoveMessage(KnownFolders.Inbox, draftMessage.ItemId);
                    MapiMessage fetchedMessage = client.FetchMessage(movedMessage.ItemId);
                }
                finally
                {
                }
~~~
### **Manage Attachments**


~~~csharp
            using (IGraphClient client = TestUtil.CreateGraphClient(user))
            {
                FolderInfoCollection folderInfoCol1 = client.ListFolders();
                FolderInfo inbox = null;
                foreach (FolderInfo folderInfo in folderInfoCol1)
                {
                    if (folderInfo.DisplayName.Equals("Inbox", StringComparison.InvariantCultureIgnoreCase))
                    {
                        inbox = folderInfo;
                        break;
                    }
                }
                MessageInfoCollection messageInfoCol = client.ListMessages(inbox.ItemId);
                MessageInfo messageInfo = messageInfoCol[0];
                MapiAttachment attachment = new MapiAttachment();
                attachment.SetProperty(KnownPropertyList.DisplayName, "DisplayName");
                attachment.SetProperty(KnownPropertyList.AttachDataBinary, new byte[1024]);
                MapiAttachment createdAttachment = client.CreateAttachment(messageInfo.ItemId, attachment);
                MapiAttachment fetchedAttachment = client.FetchAttachment(createdAttachment.ItemId);
                client.DeleteAttachment(createdAttachment.ItemId);
                MapiAttachmentCollection attachments = client.ListAttachments(messageInfo.ItemId);                
            }
~~~


## **Manage Categories**
To manage categories with MS Graph by Aspose.Email for .NET, use the following methods:
* [CreateCategory](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/methods/createcategory)
* [FetchCategory](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/methods/fetchcategory)
* [ListCategories](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/methods/listcategories)
* [UpdateCategory](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/methods/updatecategory)

~~~csharp
            using (IGraphClient client = TestUtil.CreateGraphClient(user))
            {
                string categoryName = "Category - " + Guid.NewGuid().ToString();
                CategoryPreset preset = CategoryPreset.Preset10;
                OutlookCategory category = client.CreateCategory(categoryName, preset);
                OutlookCategory fetchedCategory = client.FetchCategory(category.Id);

                List<OutlookCategory> categories = client.ListCategories();
                OutlookCategory cat = null;
                foreach (OutlookCategory c in categories)
                    if (c.DisplayName == categoryName)
                        cat = c;
                fetchedCategory.DisplayName = "Category - " + Guid.NewGuid().ToString();
                fetchedCategory.Preset = CategoryPreset.Preset11;
                OutlookCategory updatedCategory = client.UpdateCategory(fetchedCategory);

                client.Delete(category.Id);
                categories = client.ListCategories();
                cat = null;
                foreach (OutlookCategory c in categories)
                    if (c.DisplayName == categoryName)
                        cat = c;
            }
~~~
## **Manage Overrides**
To manage overrides with MS Graph by Aspose.Email for .NET, use the following methods:
* [CreateOrUpdateOverride](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/methods/createorupdateoverride) 
* [ListOverrides](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/methods/listoverrides)
* [UpdateOverride](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/methods/updateoverride)

~~~csharp
            using (IGraphClient client = TestUtil.CreateGraphClient(user))
            {
                string name = user.EMail.Substring(0, user.EMail.IndexOf("@"));
                ClassificationType focusedType = ClassificationType.Focused;
                ClassificationOverride o = client.CreateOrUpdateOverride(new MailAddress(user.EMail, name), focusedType);

                List<ClassificationOverride> list = client.ListOverrides();
                ClassificationOverride fo = null;
                foreach (ClassificationOverride co in list)
                    if (user.EMail.Equals(co.Sender.Address, StringComparison.InvariantCultureIgnoreCase))
                        fo = co;
                fo.ClassifyAs = ClassificationType.Other;
                string newName = fo.Sender.DisplayName = name + "_1";
                ClassificationOverride uo = client.CreateOrUpdateOverride(fo);
                fo.ClassifyAs = ClassificationType.Focused;
                uo = client.UpdateOverride(fo);
                client.Delete(uo.Id);
                list = client.ListOverrides();
                fo = null;
                foreach (ClassificationOverride co in list)
                    if (user.EMail.Equals(co.Sender.Address, StringComparison.InvariantCultureIgnoreCase))
                        fo = co;
            }
~~~
## **Manage Rules**
To manage rules with MS Graph by Aspose.Email for .NET, use the following methods:
* [CreateRule](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/methods/createrule)
* [FetchRule](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/methods/fetchrule)
* [UpdateRule](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/methods/updaterule)
* [ListRules](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/methods/listrules)

~~~csharp
            using (IGraphClient client = TestUtil.CreateGraphClient(user))
            {
                List<InboxRule> listedRules = client.ListRules();
                foreach(InboxRule r in  listedRules)
                    client.Delete(r.RuleId);
                try
                {
                    InboxRule rule = PrepareRule(user);
                    InboxRule createdRule = client.CreateRule(rule);
                    checkRule(rule, createdRule);
                    listedRules = client.ListRules();
                    InboxRule ruleInList = null;
                    foreach (InboxRule r in listedRules)
                        if (r.DisplayName == rule.DisplayName)
                        {
                            ruleInList = r;
                            break;
                        }
                    checkRule(rule, ruleInList);
                    InboxRule fetchedRule = client.FetchRule(createdRule.RuleId);
                    checkRule(rule, fetchedRule);
                    createdRule.DisplayName = "Test rule - " + Guid.NewGuid().ToString();
                    createdRule.IsEnabled = false;
                    InboxRule updatedRule = client.UpdateRule(createdRule);
                    checkRule(createdRule, updatedRule);
                    fetchedRule = client.FetchRule(createdRule.RuleId);
                    checkRule(createdRule, fetchedRule);
                    client.Delete(createdRule.RuleId);
                    ruleInList = null;
                    listedRules = client.ListRules();
                    foreach (InboxRule r in listedRules)
                        if (r.DisplayName == createdRule.DisplayName)
                        {
                            ruleInList = r;
                            break;
                        }
                }
                finally
                {
                    listedRules = client.ListRules();
                    foreach (InboxRule r in listedRules)
                        client.Delete(r.RuleId);
                }
            }

        private InboxRule PrepareRule(TestUser user)
        {
            string name = user.EMail.Substring(0, user.EMail.IndexOf("@"));
            InboxRule rule = new InboxRule();
            rule.DisplayName = "Test rule - " + Guid.NewGuid().ToString();
            rule.Priority = 1;
            rule.IsEnabled = true;
            rule.Conditions = new RulePredicates();
            rule.Conditions.ContainsSenderStrings = new StringCollection();
            rule.Conditions.ContainsSenderStrings.Add(name);
            rule.Actions = new RuleActions();
            rule.Actions.ForwardToRecipients = new MailAddressCollection();
            rule.Actions.ForwardToRecipients.Add(new MailAddress(user.EMail, name, true));
            rule.Actions.StopProcessingRules = true;
            return rule;
        }


        private void checkRule(InboxRule sample, InboxRule compared)
        {
            Assert.AreEqual(sample.DisplayName, compared.DisplayName);
            Assert.AreEqual(sample.Priority, compared.Priority);
            Assert.AreEqual(sample.IsEnabled, compared.IsEnabled);
            bool found = false;
            foreach (string senderString in sample.Conditions.ContainsSenderStrings)
            {
                foreach (string comparedString in compared.Conditions.ContainsSenderStrings)
                    if (comparedString.Equals(senderString, StringComparison.InvariantCultureIgnoreCase))
                        found = true;
            }
            Assert.IsTrue(found);
            Assert.AreEqual(sample.Actions.StopProcessingRules, compared.Actions.StopProcessingRules);
            foreach (MailAddress sampleAddress in sample.Actions.ForwardToRecipients)
            {
                found = false;
                foreach (MailAddress comparedAddress in compared.Actions.ForwardToRecipients)
                {
                    if (comparedAddress.DisplayName.Equals(sampleAddress.DisplayName, StringComparison.InvariantCultureIgnoreCase) &&
                        comparedAddress.Address.Equals(sampleAddress.Address, StringComparison.InvariantCultureIgnoreCase))
                        found = true;
                }
                Assert.IsTrue(found);
            }
        }
~~~
## **Manage Notebooks**
To manage notebooks with MS Graph by Aspose.Email for .NET, use the following methods:
* [CreateNotebook](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/methods/createnotebook)
* [CopyNotebook](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/methods/copynotebook)
* [FetchNotebook](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/methods/fetchnotebook)
* [ListNotebooks](https://reference.aspose.com/email/net/aspose.email.clients.graph/igraphclient/methods/listnotebooks)

~~~csharp
            using (IGraphClient client = TestUtil.CreateGraphClient(user))
            {                
                try
                {
                    NotebookCollection notebooks1 = client.ListNotebooks();
                    Notebook newNotebook = new Notebook();
                    newNotebook.DisplayName = "EMAILNET-39390 - " + Guid.NewGuid().ToString();
                    Notebook createdNotebook = client.CreateNotebook(newNotebook);
                    Notebook fetchedNotebook = client.FetchNotebook(createdNotebook.Id);
                    NotebookCollection notebooks2 = client.ListNotebooks();
                }
                finally
                {                    
                }
~~~