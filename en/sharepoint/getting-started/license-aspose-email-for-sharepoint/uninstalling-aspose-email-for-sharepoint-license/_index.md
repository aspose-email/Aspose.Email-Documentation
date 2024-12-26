---
title: Uninstalling Aspose.Email for SharePoint License
ArticleTitle: Uninstalling Aspose.Email for SharePoint License
type: docs
weight: 30
url: /sharepoint/uninstalling-aspose-email-for-sharepoint-license/
---

To uninstall the Aspose.Email for SharePoint license, use the server console or SharePoint 2010 Management Shell:

1. Retract the license solution from the farm: 

``` java

  stsadm.exe -o retractsolution -name Aspose.Email.SharePoint2010.License.wsp -immediate

```

1. Execute administrative timer jobs to complete the retraction immediately: 

``` java

 stsadm.exe -o execadmsvcjobs

```

1. Wait for the retraction to complete. Use Central Administration to check if the retraction completed: 
   1. Under **Central Administration**, select **Operations** and then **Solution Management**.
1. Remove the solution from the SharePoint solution store: 

``` java

 stsadm.exe -o deletesolution -name Aspose.Email.SharePoint2010.License.wsp

```
