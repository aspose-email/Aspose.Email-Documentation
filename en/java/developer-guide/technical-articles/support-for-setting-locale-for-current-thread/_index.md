---
title: Support for setting Locale for Current Thread
ArticleTitle: Support for setting Locale for Current Thread
type: docs
weight: 50
url: /java/support-for-setting-locale-for-current-thread/
---

Aspose.Email provides the ability to set the Locale for the current thread. Aspose.Email provides a class [CurrentThreadSettings](https://apireference.aspose.com/java/email/com.aspose.email/CurrentThreadSettings) that provides the [setLocale](https://apireference.aspose.com/java/email/com.aspose.email/CurrentThreadSettings#setLocale\(java.util.Locale\)) method for this purpose. The following code snippet demonstrates the use of the [CurrentThreadSettings](https://apireference.aspose.com/java/email/com.aspose.email/CurrentThreadSettings) class to set the current Locale. The snippet fist sets the Locale to an invalid value and then uses the [CurrentThreadSettings.setLocale](https://apireference.aspose.com/java/email/com.aspose.email/CurrentThreadSettings#setLocale\(java.lang.String\)) method to set the Locale for the current thread.



~~~Java
Locale defaultLocale = Locale.getDefault();
try {
    // set incorrect default Locale
    Locale.setDefault(new Locale("en", "RU"));
    // set Current Thread Locale
    CurrentThreadSettings.setLocale("en-US");
    // or
    // CurrentThreadSettings.setLocale(new Locale("en", "US"));

    PersonalStorage.create(dataDir + "test.pst", FileFormatVersion.Unicode);
} finally {
    Locale.setDefault(defaultLocale);
}
~~~
