---
title: "Soporte para configurar la configuración regional para el hilo actual"
url: /es/java/support-for-setting-locale-for-current-thread/
weight: 50
type: docs
---

Aspose.Email ofrece la posibilidad de establecer la configuración regional para el hilo actual. Aspose.Email proporciona una clase [CurrentThreadSettings](https://apireference.aspose.com/java/email/com.aspose.email/CurrentThreadSettings) que proporciona la [setLocale](https://apireference.aspose.com/java/email/com.aspose.email/CurrentThreadSettings#setLocale\(java.util.Locale\)) método para este propósito. El siguiente fragmento de código demuestra el uso del [CurrentThreadSettings](https://apireference.aspose.com/java/email/com.aspose.email/CurrentThreadSettings) clase para establecer la configuración regional actual. El fragmento primero establece la configuración regional en un valor no válido y, a continuación, usa el [CurrentThreadSettings.setLocale](https://apireference.aspose.com/java/email/com.aspose.email/CurrentThreadSettings#setLocale\(java.lang.String\)) método para establecer la configuración regional del hilo actual.



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