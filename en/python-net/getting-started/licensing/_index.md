---
title: Licensing
ArticleTitle: Licensing
type: docs
weight: 60
url: /python-net/licensing/
---


## **Evaluate Aspose.Email**
You can download Aspose.Email for Python via .NET free of cost for evaluation. The evaluation version provides almost all functionality of the product with certain limitations. The same evaluation version becomes licensed when you purchase a license and add a couple of lines of code to apply the license.

If you want to test Aspose.Email without evaluation version limitations, you can also request a 30 Day Temporary License. Please refer to [How to get a Temporary License?](https://purchase.aspose.com/temporary-license)
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
You can easily download an evaluation version of Aspose.Email from its download page. The evaluation version provides absolutely the same capabilities as the licensed version of Aspose.Email. Furthermore, evaluation version simply becomes licensed when you purchase a license and add a couple of lines of code to apply the license.
### **About the License**
The license is a plain text XML file that contains details such as the product name, number of developers it is licensed to, subscription expiry date and so on. The file is digitally signed, so don't modify the file. Even inadvertent addition of an extra line break into the file will invalidate it.

You need to set a license before utilizing Aspose.Email if you want to avoid its evaluation limitations. It is only required to set a license once per application (or process).
### **Apply License Using File Object**
#### **Apply License using File Object**
The easiest way to set a license, is to put the license file in the same folder as that of the dll of the component (included in Aspose.Email) and specify just the file name without its path.

``` java

 // Instantiate an instance of license and set the license file through its path

license lic = new license();

license.set_license("Aspose.Email.Python.lic");

```

When you call SetLicense method, the license name should be same as that of your license file name. For example, you may change the license file name to "Aspose.Email.Python.lic.xml". Then in your code, you should use the modified license name (that is Aspose.Email.Python.lic.xml) for the set_license method.
