---
title: Aspose.Email Java For PHP
type: docs
weight: 50
url: /java/aspose-email-java-for-php/
---

## **Introduction to Aspose.Email Java for PHP**
### **PHP / Java Bridge**
The PHP/Java Bridge is an implementation of a streaming, XML-based [network protocol](http://php-java-bridge.sourceforge.net/pjb/PROTOCOL.TXT), which can be used to connect a native script engine, for example PHP, Scheme or Python, with a Java virtual machine. It is up to 50 times faster than local RPC via SOAP, requires less resources on the web-server side. It is [faster](http://php-java-bridge.sourceforge.net/pjb/FAQ.html#performance) and more reliable than direct communication via the Java Native Interface, and it requires no additional components to invoke Java procedures from PHP or PHP procedures from Java.

Read more at [sourceforge.net](http://php-java-bridge.sourceforge.net/pjb/)
### **Aspose.Email for Java**
Aspose.Email for Java is a Java class library that enables Java applications to read and write email message files in various formats without Microsoft Outlook. It provides classes to read and update MSG,EML,EMLX,OFT files, add/remove attachments and recipients, update subject, body and other MSG file properties.
### **Aspose.Email Java for PHP**
Project Aspose.Email for PHP shows how different tasks can be performed using Aspose.Email Java APIs in PHP. This project is aimed to provide useful examples for PHP Developers who want to utilize Aspose.Email for Java in their PHP Projects using [PHP/Java Bridge](http://php-java-bridge.sourceforge.net/pjb/).

**This section includes the following topics:**

- [Download and Configure Aspose.Email in PHP](/email/java/download-and-configure-aspose-email-in-php/)
- [PHP Programmers Guide](/email/java/php-programmers-guide/)
  - [Programming Email in PHP](/email/java/programming-email-in-php/)
    - [Converting Email Messages in PHP](/email/java/converting-email-messages-in-php/)
    - [Create New Email in PHP](/email/java/create-new-email-in-php/)
    - [Displaying Email Information on Screen in PHP](/email/java/displaying-email-information-on-screen-in-php/)
    - [Extracting Email Headers in PHP](/email/java/extracting-email-headers-in-php/)
    - [Manage Attachments in Email Message in PHP](/email/java/manage-attachments-in-email-message-in-php/)
    - [Save Message as Draft in PHP](/email/java/save-message-as-draft-in-php/)
    - [Update and Save an Email in PHP](/email/java/update-and-save-an-email-in-php/)
  - [Programming Outlook in PHP](/email/java/programming-outlook-in-php/)
    - [Working with Outlook Message (MSG) Files in PHP](/email/java/working-with-outlook-message-msg-files-in-php/)
      - [Creating and Saving Outlook Contacts in PHP](/email/java/creating-and-saving-outlook-contacts-in-php/)
      - [Creating and Saving Outlook Notes in PHP](/email/java/creating-and-saving-outlook-notes-in-php/)
      - [Parsing Outlook Message Files in PHP](/email/java/parsing-outlook-message-files-in-php/)
    - [Working with Outlook Personal Storage (PST) Files in PHP](/email/java/working-with-outlook-personal-storage-pst-files-in-php/)
      - [Adding Files to PST in PHP](/email/java/adding-files-to-pst-in-php/)
      - [Adding MapiCalendar to PST in PHP](/email/java/adding-mapicalendar-to-pst-in-php/)
      - [Adding MapiContact to PST in PHP](/email/java/adding-mapicontact-to-pst-in-php/)
      - [Adding MapiJournal to PST in PHP](/email/java/adding-mapijournal-to-pst-in-php/)
      - [Adding MapiTask to PST in PHP](/email/java/adding-mapitask-to-pst-in-php/)
      - [Create New PST in PHP](/email/java/create-new-pst-in-php/)
      - [Search Messages and Folders in a PST by Some Criteria in PHP](/email/java/search-messages-and-folders-in-a-pst-by-some-criteria-in-php/)
      - [String Searching in PST with Ignore Case in PHP](/email/java/string-searching-in-pst-with-ignore-case-in-php/)
- [Support, Extend and Contribute to Aspose.Email in PHP](/email/java/support-2c-extend-and-contribute-to-aspose-email-in-php/)
## **System Requirements and Supported Platforms**
### **System Requirements**
**Following are the system requirements to use Aspose.Email Java for PHP:**

- Tomcat Server 8.0 or above installed.
- PHP/JavaBridge is configured.
- FastCGI is installed.
- Downloaded Aspose.Email component.
### **Supported Platforms**
**Following are the supported platforms:**

- PHP 5.3 or above
- Java 1.8 or above
## **Downloads and Configure**
### **Download Required Libraries**
Download required libraries mentioned below. These are the required for executing Aspose.Email Java for PHP examples.

- **Aspose:** [Aspose.Email for Java Component](https://downloads.aspose.com/total)
- [PHP/Java Bridge](http://citylan.dl.sourceforge.net/project/php-java-bridge/Binary%20package/php-java-bridge_6.2.1/php-java-bridge_6.2.1_documentation.zip)
### **Download Examples from Social Coding Sites**
Following releases of running examples are available to download on below mentioned social coding sites:

-----
#### **GitHub**
- **Aspose.Email Java for PHP Examples** 
  - [Aspose.Email Java for PHP](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_Java_for_PHP)
#### **CodePlex**
- **Aspose.Email Java for PHP Examples** 
  - [Aspose.Email Java for PHP](https://archive.codeplex.com/?p=asposeemailjavaphp)
### **How to configure the source code on Linux Platform**
Please follow these simple steps in order to open and extend the source code while using:
### **1. Install Tomcat Server**
To install tomcat server, issue following command on the linux console. This will successfully install tomcat server. 

``` actionscript3

 sudo apt-get install tomcat8

```
### **2. Download and Configure PHP/JavaBridge**
In order to download the PHP/JavaBridge binaries, issue following command on the linux console. 

``` actionscript3

  wget http://citylan.dl.sourceforge.net/project/php-java-bridge/Binary%20package/php-java-bridge_6.2.1/php-java-bridge_6.2.1_documentation.zip 

```


Unzip the PHP/JavaBridge binaries by issuing the following command on linux console. 

``` actionscript3

  unzip -d php-java-bridge_6.2.1_documentation.zip 

```


This will extract **JavaBridge.war** file. Copy it to tomcat88 **webapps** folder by issuing the following command on Linux console. 

``` actionscript3

  sudo cp JavaBridge.war /var/lib/tomcat8/webapps/JavaBridge.war 

```


By copying, tomcat8 will automatically create a new folder "**JavaBridge**" in **webapps**. Once the folder is created, make sure your tomcat8 is running and then check <http://localhost:8080/JavaBridge> in browser, it should open a default page of JavaBridge. 

If any error message appears then install  **FastCGI** by issuing the following command on Linux console.

``` actionscript3

  sudo apt-get install php55-cgi 

```

After installing php5.5 cgi, restart tomcat8 server and check <http://localhost:8080/JavaBridge> again in the browser.

If **JAVA_HOME** error is displayed, then open /etc/default/tomcat8 file and uncomment the line that sets the JAVA_HOME. Check <http://localhost:8080/JavaBridge> in browser again, it should come with PHP/JavaBridge Examples page. 
### **3. Configure Aspose.Email Java for PHP Examples**
Clone, PHP examples by issuing the following commands inside webapps/JavaBridge folder.  

``` actionscript3

 $ git init&nbsp;

$ git clone [https://github.com/asposeslides/Aspose.Email-for-Java/tree/master/Plugins/Aspose.Email-for-Java_for_PHP] 

```

### **How to configure the source code on Windows Platform**
Please follow below simple steps to configure PHP/Java Bridge on Windows Platform

1. Install PHP5 and configure as you normally do
2. Install JRE 6 (Java Runtime Environment) if you don’t already have it. You can check this in C:\Program Files etc. You can download it here . I am using JRE 6 as It is compatible with PHP Java Bridge (PJB).

3. Install Apache Tomcat 8.0. You can download it here

4.Download [JavaBridge.war](https://sourceforge.net/projects/php-java-bridge/files/Binary%20package/php-java-bridge_6.2.1/JavaBridgeTemplate621.war/download). Copy this file to tomcat webapps directory.
(ex: `C:\Program Files\Apache Software Foundation\Tomcat 8.0\webapps` )

5. Restart tomcat apache service.

6.Go to <http://localhost:8080/JavaBridge/test.php> to check if php works. You can find other examples in there

7.Copy your [Aspose.Email Java](https://downloads.aspose.com/total) jar file to `C:\Program Files\Apache Software Foundation\Tomcat 8.0\webapps\JavaBridge\WEB-INF\lib`

8. Clone [Aspose.Email Java for PHP](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_Java_for_PHP) examples inside `C:\Program Files\Apache Software Foundation\Tomcat 8.0\webapps\` folder.

8. Copy folder `C:\Program Files\Apache Software Foundation\Tomcat 8.0\webapps\JavaBridge\java` to your Aspose.Email Java for PHP examples folder.

\10. Restart apache tomcat service and start using examples. 
