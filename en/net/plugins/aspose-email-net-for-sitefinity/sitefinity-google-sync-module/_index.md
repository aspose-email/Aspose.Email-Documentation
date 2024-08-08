---
title: Sitefinity Google Sync Module
type: docs
weight: 20
url: /net/sitefinity-google-sync-module/
---


## **Introduction**
### **Google Sync Module**
Sitefinity Google Sync is an open source add-on from [Aspose](http://www.aspose.com/) that links your Sitefinity users to Google/Gmail contacts without requiring any other software. It uses powerful features of [Aspose.Email for .NET](http://www.aspose.com/.net/email-component.aspx) to allow you to easily sync your Google contacts and Sitefinity users.

This initial version of the module is enriched with the following features to make the sync process effective, simple and easy to use.

- Google/Gmail server credentials are encrypted and saved in the database so that you don’t have to enter them every time you use the module.
- Sync all or selected Gmail contacts to Google and vice versa.
- Option to select one or more Sitefinity user when performing Google/Gmail to Sitefinity sync.
- Existence of every contact/user in the destination system is checked before migration to make sure that the sync does not create duplicate records.
- The contacts migrated to Google/Gmail are put in Other Contacts group so that you can verify and move only required ones to My Contacts.
- A brief summary of the sync process is shown upon completion. 

![todo:image_alt_text](http://www.aspose.com/blogs/wp-content/uploads/2015/01/Aspose-.NET-Google-Sync-for-Sitefinity.png)

![todo:image_alt_text](http://www.aspose.com/blogs/wp-content/uploads/2015/01/Google-to-Sitefinity-Sync.png)

![todo:image_alt_text](http://www.aspose.com/blogs/wp-content/uploads/2015/01/Sitefinity-to-Google-Sync.png)
## **Support, Extend and Contribute**
### **Support**
From the very first days of Aspose, we knew that just giving our customers good products would not be enough. We also needed to deliver good service. We are developers ourselves and understand how frustrating it is when a technical issue or a quirk in the software stops you from doing what you need to do. We're here to solve problems, not create them.

This is why we offer free support. Anyone who uses our product, whether they have bought them or are using an evaluation, deserves our full attention and respect.

You can log any issues or suggestions related to Aspose .NET Exchange/Gmail Sync for Sitefinity Module using any of the following platforms

- [CodePlex ](https://asposesitefinity.codeplex.com/workitem/list/basic)
- [Github ](https://github.com/asposemarketplace/Aspose_for_Sitefinity/issues)
- [Sourceforge ](https://sourceforge.net/p/asposesitefinity/tickets/?source=navbar)
- [Bitbucket ](https://bitbucket.org/asposemarketplace/aspose-for-sitefinity/issues?status=new&status=open)

**Aspose .NET Exchange Sync for Sitefinity**

- [Microsoft Developer Network - Q and A ](https://code.msdn.microsoft.com/Aspose-NET-Exchange-Sync-1741397f/view/Discussions#content)

**Aspose .NET Google Sync for Sitefinity**

- [Microsoft Developer Network - Q and A ](https://code.msdn.microsoft.com/Sync-Sitefinity-Users-with-f8edd30b/view/Discussions#content)
### **Extend and Contribute**
Aspose .NET Exchange Sync for Sitefinity and Aspose .NET Google Sync for Sitefinity are open source and their source code is available on the major social coding websites listed below. Developers are encouraged to download the source code and extend the functionality as per their own requirements.
### **Source Code**
You can get the latest source code from one of the following locations

- [CodePlex ](https://asposesitefinity.codeplex.com/SourceControl/latest)
- [Github ](https://github.com/asposemarketplace/Aspose_for_Sitefinity)
- [Sourceforge ](https://sourceforge.net/p/asposesitefinity/code/ci/master/tree/)
- [Bitbucket ](https://bitbucket.org/asposemarketplace/aspose-for-sitefinity/src)
### **How to configure the source code**
You need to have the following installed in order to open and extend the source code

- Visual Studio 2010 or higher

Please follow these simple steps to get started

1. Download/Clone the source code.
1. Open Visual Studio 2010 and Choose **File** > **Open Project**
1. Browse to the latest source code that you have downloaded and open **Aspose.ExchangeSync.sln** or **Aspose.GoogleSync.sln**
## **System Requirements and Supported Platforms**
### **System Requirements**
In order to setup Aspose .NET Exchange/Google Sync for Sitefinity add-on you need to have the following requirements met:

- Sitefinity CMS running on ASP.NET 4.0

Please feel free to contact us if you have any issues setting up this Sitefinity Add-on.
### **Supported Platforms**
The module is supported on all versions of

- Sitefinity CMS running on ASP.NET 4.0

## **Downloading and Installing**
### **Downloading**
You can download Aspose .NET Google Sync for Sitefinity from one of the following locations

- [CodePlex ](https://asposesitefinity.codeplex.com/releases)
- [Github ](https://github.com/asposemarketplace/Aspose_for_Sitefinity/releases)
- [Sourceforge ](https://sourceforge.net/projects/asposesitefinity/files/)
- [Bitbucket ](https://bitbucket.org/asposemarketplace/aspose-for-sitefinity/downloads)
### **Installing**
Once downloaded, please follow these steps to install the Add-on into your Sitefinity website:

**Step 1: Copy files to your Sitefinity installation**

Please extract the downloaded ZIP file. You will need FTP or direct access to the Sitefinity installation folder on the server to perform the following:

1. Copy Aspose.Email.dll and Aspose.SiteFinity.GoogleSync.dll into the **bin** folder of the Sitefinity installation.
1. Copy the **Addons** folder on the root of the Sitefinity installation where the **bin** folder is located.

**Step 2: Register the Aspose .NET Google Sync for Sitefinity add-on in Sitefinity**

1. Log into your Sitefinity CMS with an ‘**Administrator**’ account. The login page can be reached by <http://www.mywebsite.com/sitefinity>
1. Click **Administration** and then **Settings**.
   The Basic Settings page appears.
1. **Click the Advanced** **link.** 
   The Settings page appears.
1. In the left pane, click **Toolboxes** followed by **Toolboxes**, then **PageControls**, **Sections** and **ContentToolboxSection**, then **Tools.**
1. Click **Create new**.
   The widget registration form appears.
1. Fill the form fields as follows: 
   1. Make sure **Enabled** is selected.
   1. Add ~/Addons/AsposeGoogleSync/AsposeGoogleSync.ascx in the **Control CLR Type or Virtual Path** field.
   1. Add **Name**, **Title** and **Description** as follows:
      AsposeGoogleSync
      Aspose Google Sync
      Sync Sitefinity Users with Google Contacts using Aspose .NET Google Sync for Sitefinity
   1. You may leave all other fields as they are.
1. When finished, click **Save changes**.
   The widget is registered in the toolbox and can be used in Sitefinity. The settings are also shown in the picture below 

![todo:image_alt_text](http://www.aspose.com/blogs/wp-content/uploads/2015/01/How-to-register-Aspose-.NET-Google-Sync-for-Sitefinity.png)
## **Using and Video Demo**
### **Using**
After you have installed and configured the Aspose .NET Google Sync for Sitefinity add-on it is really simple to start using it on your website. Please follow these simple steps to get started:

1. Make sure you are logged-in to Sitefinity with an Administrator level account.
1. Navigate to the page where you want to add the Google Sync add-on. Make sure the page is opened in edit mode.
1. From the **Drag Widgets** menu on the right, select Aspose Google Sync and drag it into position.

![todo:image_alt_text](http://www.aspose.com/blogs/wp-content/uploads/2015/01/Using-Aspose-.NET-Google-Sync-for-Sitefinity.png)

You have successfully installed and added Aspose .NET Google Sync for Sitefinity Module to your page. You will be presented with three simple options to get started 

- Google to Sitefinity Sync
- Sitefinity to Google Sync
- Google Settings

You will asked to enter Google Server details when clicking on any option for the first time. A simple form takes all the required details to connect to your Google account and then these details will be encrypted and saved in the database for later use.

![todo:image_alt_text](http://www.aspose.com/blogs/wp-content/uploads/2015/01/Google-server-details.png)

Once the sync process is completed, a brief summary of migrated records count and list of records that already existed and are not imported is shown.
### **Video Demo**
Please check [the video](https://www.youtube.com/watch?v=N3Vv4Bh84Zw) below to see the module in action.
