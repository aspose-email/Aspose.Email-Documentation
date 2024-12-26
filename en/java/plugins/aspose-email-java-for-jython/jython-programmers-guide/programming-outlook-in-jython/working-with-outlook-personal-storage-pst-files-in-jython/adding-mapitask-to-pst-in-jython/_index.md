---
title: Adding MapiTask to PST in Jython
ArticleTitle: Adding MapiTask to PST in Jython
type: docs
weight: 50
url: /java/adding-mapitask-to-pst-in-jython/
---

## **Aspose.Email - Adding MapiTask to PST**
To Add MapiTask to PST using **Aspose.Email Java for Jython**, simply invoke **AddMapiTaskToPST** module. Here you can see example code.

**Jython Code**

{{< highlight python >}}

 from aspose-email import Settings

from com.aspose.email import MapiTask

from com.aspose.email import MapiTaskHistory

from com.aspose.email import MapiTaskOwnership

from com.aspose.email import PersonalStorage

from com.aspose.email import FileFormatVersion

from com.aspose.email import StandardIpmFolder

from java.util import Date

from java.util import Calendar

class AddMapiTaskToPST:

    def __init__(self):



        dataDir = Settings.dataDir + 'ProgrammingOutlook/WorkingWithOutlookPersonalStorage/AddMapiTaskToPST/'



        task = MapiTask("To Do", "Just click and type to add task", Date(), Date())

        task.setPercentComplete(20)

        task.setEstimatedEffort(2000)

        task.setActualEffort(20)

        mapiTaskHistory=MapiTaskHistory()

        task.setHistory(mapiTaskHistory.Assigned)

        task.setLastUpdate(Date())

        task.getUsers().setOwner("Darius")

        task.getUsers().setLastAssigner("Harkness")

        task.getUsers().setLastDelegate("Harkness")

        mapiTaskOwnership=MapiTaskOwnership()

        task.getUsers().setOwnership(mapiTaskOwnership.AssignersCopy)

        personalStorage=PersonalStorage()

        fileFormatVersion=FileFormatVersion

        pst = personalStorage.create(dataDir + "TaskPST.pst", fileFormatVersion.Unicode)

        standardIpmFolder=StandardIpmFolder

        task_folder = pst.createPredefinedFolder("Tasks",standardIpmFolder.Tasks)

        task_folder.addMapiMessageItem(task)

        print "Added MapiTask Successfully."





if __name__ == '__main__':        

    AddMapiTaskToPST()

{{< /highlight >}}
## **Download Running Code**
Download **Adding MapiTask to PST (Aspose.Email)** from any of the below mentioned social coding sites:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Jython-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavajython)
