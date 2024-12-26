---
title: Create New PST in Python
ArticleTitle: Create New PST in Python
type: docs
weight: 50
url: /java/create-new-pst-in-python/
---

## **Aspose.Email - Create New PST**
To Create New PST using **Aspose.Email Java for Python**, Use following code.

**Python Code**

``` python



\# Create an instance of PersonalStorage

personalStorage = self.PersonalStorage

pst = personalStorage.create(self.dataDir + "sample1.pst", 0)

\# Create a folder at root of pst

pst.getRootFolder().addSubFolder("myInbox")

\# Add message to newly created folder

mapi_message = self.MapiMessage

pst.getRootFolder().getSubFolder("myInbox").addMessage(mapi_message.fromFile(self.dataDir + "Message.msg"))

print "Created PST successfully."

```
## **Download Running Code**
Download **Create New PST (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavapython)
