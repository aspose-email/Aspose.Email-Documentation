---
title: Managing PST File Password Protection 
ArticleTitle: Working with PST Password Protection Properties
type: docs
weight: 110
url: /python-net/working-with-pst-password-protection-properties/
---


Microsoft Outlook allows users to protect PST files with passwords to restrict access to them. Aspose.Email can detect password protection on a PST file. 

This article covers the following issues:

- Check PST File Password Protection 
- Read Password-Protected PST Files
- Validate Password in Password Protected PST
- Add/Change/Remove Password in PST Files

## **Check PST File Password Protection**

To check if a PST file is protected with a password, use the *is_password_protected* method of the [MessageStore](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/messagestore/#messagestore-class) class as shown in the code sample below: 

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

print(f"The storage is password protected - {pst.store.is_password_protected}")
```

## **Read Password-Protected PST Files**

You can read password-protected files just like regular unprotected PST files. The following code snippet allows you to access each individual message with the possibility of its further processing:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

for folder in pst.root_folder.get_sub_folders():
    for msg in folder.enumerate_messages():
    # do something
```

## **Validate PST Passwords**

To check if a password in a PST file is valid, Aspose.Email provides the *is_password_valid(password)* method of the [MessageStore](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/messagestore/#messagestore-class) class. It takes the string password as a parameter and returns True if the password is correct and False if it is incorrect.

The following code snippet demonstrates the use of *is_password_valid(password)* method:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

print(f"Password is valid - {pst.store.is_password_valid('Password1')}")
```

## **Add, Change, or Remove PST Passwords**

The *change_password(password)* method of the [MessageStore](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/messagestore/#messagestore-class) class is used to manipulate passwords in PST files. The following code sample shows how to add, change or remove a password:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.create("SetPasswordOnPST_out.pst", ae.storage.pst.FileFormatVersion.UNICODE)
# Add or change the password
password = "Password1"
pst.store.change_password(password)
# Remove the password
pst.store.change_password(None)
```
