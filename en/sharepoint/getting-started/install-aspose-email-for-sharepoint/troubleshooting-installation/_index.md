---
title: Troubleshooting Installation
ArticleTitle: Troubleshooting Installation
type: docs
weight: 40
url: /sharepoint/troubleshooting-installation/
---


## **Error: Some or all identity references could not be translated**
If you see errors like “Some or all identity references could not be translated”, you may run the following command to resolve them.

**[DOS]**

``` cs



stsadm.exe -o updatefarmcredentials -userlogin <DOMAIN\username> -password <password>



```

{{% alert color="primary" %}} 

If the "Some or all identity references" error message appears, you may also need to reset IIS services using “iisreset” or restart the operating system. 

![todo:image_alt_text](troubleshooting-installation_1.png)

{{% /alert %}}
