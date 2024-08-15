---
title: Licensing
type: docs
weight: 60
url: /java/licensing/
---

{{% alert color="primary" %}} 

You can download an evaluation version of **Aspose.Email** for Java from its download page. The evaluation version provides absolutely the same capabilities as the licensed version of the product. Furthermore, evaluation version simply becomes licensed when you purchase a license and add a couple of lines of code to apply the license.

Once you are happy with your evaluation of **Aspose.Email**, you can purchase a license at the Aspose website. Make yourself familiar with the different subscription types offered. If you have any questions, do not hesitate to contact the Aspose sales team.

Every Aspose license carries a one-year subscription for free upgrades to any new versions or fixes that come out during this time. Technical support is free and unlimited and provided both to licensed and evaluation users.

{{% /alert %}} {{% alert color="primary" %}} 

If you want to test **Aspose.Email** without evaluation version limitations, request a 30-day temporary license. Please refer to [How to get a Temporary License?](https://purchase.aspose.com/temporary-license) for more information.

{{% /alert %}} 
## **Evaluation Version Limitations**
Evaluation version of Aspose.Email (without a license specified) provides full product functionality except few of its components like Aspose.Email.Mail, Aspose.Email.Pop3,and Aspose.Email.Imap that contain some evaluation limitations.

1. License.txt file is added to the message file saved using Aspose.Email
1. Only 50 emails can be extracted from a folder in PST file
1. Only 3 attachments as well as inline images can be extracted from an MSG file
1. Max number of processed attacments in CFB format is 1
1. Max number of processed recipients in CFB format is 1
1. Adds "Evaluation Message" in Subject during saving in CFB,EML or MSG formats
1. End Date can't be later then 31-12-2004 in GenerateOccurrences method of the recurrence pattern. This allows you to test the product meaningfully, yet impossible to use in a production application. For example, you can create a pattern such as "start on January 1, 2000 and repeat every last working day of a month" and generate occurrences for it. Occurrences after December 31, 2004 will not be generated in the evaluation mode
1. Adds "Evaluation Watermark Image" during saving in XPS or TIFF formats.
1. Max number of ambiguous e-mail addresses and display names resolved by MS Exchange Server is 20
1. Max length of data file allowed to be drag-and-dropped with FileDropPanel is 51200 bytes
1. Shows Message box with "Evaluation Message" during a drag-and-drop operation used by FileDropPanel
1. Only 1 file is extracted from given MSO stream by InlineAttachmentExtractor.EnumerateMsoPackage method
### **Setting a License**
The license is a plain text XML file that contains details such as the product name, number of developers it is licensed to, subscription expiry date and so on. The file is digitally signed, so do not modify the file; even the inadvertent addition of an extra line break into the file will invalidate it.

You need to apply a license if you want to avoid the evaluation limitations. You are only required to set a license once per application or process.

The license can be loaded from a stream or file in the following locations:

1. Explicit path.
1. The folder that contains the Aspose.Email.jar.

Use the License.setLicense method to license the component. Often the easiest way to set a license is to put the license file in the same folder as Aspose.Email.jar and specify just the file name without path as shown in the following example:
#### **Setting License from File**
In this example **Aspose.Email** will attempt to find the license file in the folder that contain the JARs of your application.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-licensing-ApplyLicenseFromFile-ApplyLicenseFromFile.java" >}}
#### **Setting License from Stream**
Initializes a license from a stream.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-licensing-ApplyLicenseFromFile-ApplyLicenseFromStream.java" >}}
### **Apply Metered License**
Aspose.Email allows developers to apply metered key. It is a new licensing mechanism. The new licensing mechanism will be used along with existing licensing method. Those customers who want to be billed based on the usage of the API features can use the metered licensing. For more details, please refer to [Metered Licensing FAQ](https://purchase.aspose.com/faqs/licensing/metered) section.

A new class Metered has been introduced to apply metered key. Following is the sample code demonstrating how to set metered public and private keys.

{{< gist "" "e3443fa9baa07df6d929fc4a408add67" "Examples-src-main-java-com-aspose-email-examples-licensing-ApplyMeteredLicense-ApplyMeteredLicense.java" >}}
## **Including the License File as an Embedded**
### **Validate the License**
It is possible to validate if the license has been set properly or not. The [License](http://www.aspose.com/api/java/email/com.aspose.email/classes/License) class has the isLicensed field that will return true if license has been properly set.

**Java**

``` cs

 License license = new License();

license.setLicense("Aspose.Email.Java.lic");

if (License.isLicensed()) {

    System.out.println("License is Set!");

}

```


