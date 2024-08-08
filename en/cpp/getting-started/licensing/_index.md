---
title: Licensing
type: docs
weight: 60
url: /cpp/licensing/
description: Evaluate Email C++ Library API and apply license using file or stream object.
---

## **Evaluation Version Limitations**
A free evaluation version of Aspose.Email for C++ can be downloaded from the downloads section of Aspose's web site at: https://releases.aspose.com/email/cpp/

## **Apply License using File or Stream Object**
The license can be loaded from a file or stream object. Aspose.Eamil for C++ will try to find the license in the following locations:

1. Explicit path.
1. The folder that contains Aspose.Cells.dll.
1. The folder that contains the assembly that called Aspose.Cells.dll.
1. The folder that contains the entry assembly (your .exe).
1. An embedded resource in the assembly that called Aspose.Cells.dll.

The easiest way to set a license is to put the license file in the same folder as the Aspose.Email.dll file and specify the file name, without a path, as shown in the example below.
### **Loading a License from File**
The easiest way to apply a license is to put the license file in the same folder as the Aspose.Email.dll file and specify just the file name without a path.

{{% alert color="primary" %}} 

When you call the SetLicense method, the license name that you pass should be that of the license file. For example, if you change the license file name to "Aspose.Email.lic" pass that file name to the Emails->SetLicense(…) method.

{{% /alert %}} 

**C++**

``` cs

 intrusive_ptr<License> license = new License();

license->SetLicense(new String("Aspose.Email.lic"));

```
### **Loading a License from a Stream Object**
The following example shows how to load a license from a stream.

**C++**

``` cs

 intrusive_ptr<License>license = new License();

intrusive_ptr<FileStream> myStream = new FileStream(new String("Aspose.Email.lic"), FileMode_Open);

license->SetLicense(myStream);

```
