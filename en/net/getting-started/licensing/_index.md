---
title: Licensing
type: docs
weight: 80
url: /net/licensing/
---


## **Evaluate Aspose.Email**
You can download Aspose.Email for .NET free of cost for evaluation. The evaluation version provides almost all functionality of the product with certain limitations. The same evaluation version becomes licensed when you purchase a license and add a couple of lines of code to apply the license.

If you want to test Aspose.Email without evaluation version limitations, you can also request a 30 Day Temporary License. Please refer to [How to get a Temporary License?](https://purchase.aspose.com/temporary-license)
### **Evaluation Version Limitations**
Evaluation version of Aspose.Email (without a license specified) provides full product functionality except some evaluation limitations.

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
## **Applying a License**
You can easily download an evaluation version of Aspose.Email from its [download page](https://www.nuget.org/packages/Aspose.Email/). The evaluation version provides absolutely the same capabilities as the licensed version of Aspose.Email. Furthermore, evaluation version simply becomes licensed when you purchase a license and add a couple of lines of code to apply the license.
### **About the License**
The license is a plain text XML file that contains details such as the product name, number of developers it is licensed to, subscription expiry date and so on. The file is digitally signed, so don't modify the file. Even inadvertent addition of an extra line break into the file will invalidate it.

You need to set a license before utilizing Aspose.Email if you want to avoid its evaluation limitations. It is only required to set a license once per application (or process).
### **Apply License Using File or Stream Object**
#### **Setting a License in Aspose.Email for .NET**
In Aspose.Email, license can be loaded from a file, stream or an embedded resource.Aspose.Email tries to find the license in the following locations:

- Explicit path
- The folder that contains the dll of the component (included in Aspose.Email)
- The folder that contains the assembly that called the dll of the component (included in Aspose.Email)
- The folder that contains the entry assembly (your .exe)
- An embedded resource in the assembly that called the dll of the component (included in Aspose.Email) There are two common methods to set the license, which are discussed below:
#### **Apply License using File or Stream Object**
The easiest way to set a license, is to put the license file in the same folder as that of the dll of the component (included in Aspose.Email) and specify just the file name without its path.



``` java

 // Instantiate an instance of license and set the license file through its path

Aspose.Email.License license = new Aspose.Email.License();

license.SetLicense("Aspose.Email.lic");

```

``` java

 // Instantiate an instance of license and set the license through a stream

Aspose.Email.License license = new Aspose.Email.License();

license.SetLicense(myStream);

```



When you call SetLicense method, the license name should be same as that of your license file name. For example, you may change the license file name to "Aspose.Email.lic.xml". Then in your code, you should use the modified license name (that is Aspose.Email.lic.xml) for the SetLicense method.
### **Apply Metered License**
Aspose.Email allows developers to apply metered key. It is a new licensing mechanism. The new licensing mechanism will be used along with existing licensing method. Those customers who want to be billed based on the usage of the API features can use the metered licensing. For more details, please refer to [Metered Licensing FAQ](https://purchase.aspose.com/faqs/licensing/metered) section.

A new class Metered has been introduced to apply metered key. Following is the sample code demonstrating how to set metered public and private keys.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Licensing-ApplyMeteredLicense-ApplyMeteredLicense.cs" >}}
## **Including the License File as an Embedded Resource**
Another neat way of packaging the license with your application and making sure it will not be lost, is to include it as an embedded resource into one of the assemblies that calls the dll of the component (included in Aspose.Email). To include the license file as an embedded resource, perform the following steps:

- In Visual Studio .NET, include the license (.lic) file into the project using the File | Add Existing Item... menu
- Select the file in the Solution Explorer and set Build Action to Embedded Resource in the Properties window
- To access the license embedded in the assembly (as embedded resource), it is not needed to call GetExecutingAssembly and GetManifestResourceStream methods of System.Reflection.Assembly class of Microsoft .NET Framework. All is needed to do, is to just add the license file as an embedded resource to your project and pass the name of the license file into SetLicense License method. The Licenseclass will automatically find the license file in the embedded resources.

Please review the example given below to understand this method of setting license (embedded) in your applications.



``` java

 // Instantiate the License class

Aspose.Email.License license = new Aspose.Email.License();

// Pass only the name of the license file embedded in the assembly

license.SetLicense("Aspose.Email.lic");

```
