---
title: Creating Simple Application
type: docs
weight: 10
url: /androidjava/creating-simple-application/
---

## **How to use Aspose.Emil for Android via Java**
This topic will guide you through the necessary steps by setup Aspose.Email for Android via Java in Android Studio IDE, assuming that you already have the latest version of Android Studio installed on your machine and you have also acquired the latest version of Aspose.Email for Android via Java package.

{{% alert color="primary" %}} 

If you haven't installed the Android Studio yet, you have to first acquire the setup of Android Studio and install it on your machine. You can download the latest version of Android Studio from [here ](https://developer.android.com/studio/index.html#win-bundle)whereas the details on how to install the IDE are available [here](https://developer.android.com/studio/install.html).

{{% /alert %}} {{% alert color="primary" %}} 

Aspose.Email for Android via Java package can be downloaded from [here](https://downloads.aspose.com/email/androidjava). Please note, each release package of Aspose.Email for Android via Java mainly consists of 2 files as detailed below.

- aspose-email-x.x.x.jar is the main library file containing all the namespaces from Aspose.Email for Android via Java API.
- aspose-email-x.x.x-libs.apk is the APK containing the 3rd party bcprov-jdk15-146.jar used for encryption and decryption facilities offered by Aspose.Email for Android via Java API.

{{% /alert %}} 
## **Getting Started with Aspose.Email for Android via Java in Android Studio**
Once the Android Studio IDE loads, click on File > New > New Project as shown below.

![todo:image_alt_text](run_examples_1.png)

You can also create a new project from the Android Studio's Welcome Screen as shown below.

![todo:image_alt_text](run_examples_2.png)

Next, you will be prompt to specify the application name, domain & location to store the project files. You can choose to change the default values as per your your choice or let them as they are, and click Next.

![todo:image_alt_text](run_examples_3.png)

In next step, you have to specify the Android Device you wish to host/run your application. Once selected, click on Next button.

![todo:image_alt_text](run_examples_4.png)

Now you need to select the Activity from a predefined list of templates. In order to keep the demonstration simple, we have selected the Empty Activity template as shown below.

![todo:image_alt_text](run_examples_5.png)

Click on Finish button on the Customize the Activity dialog as we will keep all the default settings as they are.

![todo:image_alt_text](run_examples_6.png)

As soon as you click on the Finish button on the previous step, the IDE will start building the project as shown below. Let it finish or click Cancel button.

![todo:image_alt_text](run_examples_7.png)

Now the project has been loaded in the IDE, however, you may wish to change the view to Project so that you can view the complete hierarchy of the project files. In order to change the view, please check the following snapshot.

![todo:image_alt_text](run_examples_8.png)

After changing the view to Project, find & load the build.gradle file in the editor and paste the following snippet as shown below.


~~~Java

 dexOptions{

    javaMaxHeapSize "4g"

}

~~~

![todo:image_alt_text](run_examples_9.png)

Next, we will add the Aspose.Email for Android via Java Jar to the project. There are 2 important steps as detailed below.

- Manually copy the Aspose.Email for Android via Java Jar to the \app\libs folder.
- Add Aspose.Email for Android via Java Jar as Library to the module as shown below.

![todo:image_alt_text](run_examples_10.png)

You will be prompt to select the module to which you wish to add the Aspose.Email for Java.Android Jar as library. Please choose appropriately and click OK.

![todo:image_alt_text](run_examples_11.png)

You also need to add the APK file to the project. You have to copy the APK to the \app\src\main\assets folder. If you do not have the assets folder under the main folder, you can create one by right clicking the main node in the Project view. Select New > Folder > Asset Folder.

![todo:image_alt_text](run_examples_12.png)

Once the APK has been added to the project, it needs to be loaded by the project. There are 2 ways to load the APK as follow.

- Load the APK in a custom application class using the snippet provided below, and register the custom application class to the AndroidManifest.xml.


~~~Java

 LibsLoadHelper.loadLibs(this);

~~~

- Load the APK in the OnCreate method of MainActivity.


~~~Java

 LibsLoadHelper.loadLibs(getApplicationContext());

~~~

Now we are ready to write the code. In order to keep the demonstration easy to understand, we have added a Button widget to the layout and going to handle its click event as follow.


~~~Java

private class TestEmail extends AsyncTask<Void, String, Boolean> 

{

    @Override

    protected Boolean doInBackground(Void... params) 

    {

        Boolean result = false;

        try 

        {

            //Create an instance of PersonalStorage

            com.aspose.email.PersonalStorage pst = com.aspose.email.PersonalStorage.create("newSample_out.pst", 0);

            //Create a folder at root of PST

            pst.getRootFolder().addSubFolder("myInbox");

            //Add message to newly created folder

            pst.getRootFolder().getSubFolder("myInbox").addMessage(com.aspose.email.MapiMessage.fromFile("message.msg"));

        } 

        catch (Exception e) 

        {

            e.printStackTrace();

        }

        return result;

    }

}

~~~

When you run the application using the play button on IDE interface (or using SHIFT + F10) the emulator will load the application as shown below.

![todo:image_alt_text](run_examples_13.png)

Clicking the button on the emulator will execute the code.
