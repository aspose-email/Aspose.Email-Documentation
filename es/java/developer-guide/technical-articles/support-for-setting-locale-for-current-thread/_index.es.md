---
title: "Soporte para establecer la configuración regional para el hilo actual"
url: /es/java/support-for-setting-locale-for-current-thread/
weight: 50
type: docs
---

Aspose.Email proporciona la capacidad de establecer la configuración regional para el hilo actual. Aspose.Email ofrece una clase [CurrentThreadSettings](https://apireference.aspose.com/java/email/com.aspose.email/CurrentThreadSettings) que proporciona el método [setLocale](https://apireference.aspose.com/java/email/com.aspose.email/CurrentThreadSettings#setLocale\(java.util.Locale\)) para este propósito. El siguiente fragmento de código demuestra el uso de la clase [CurrentThreadSettings](https://apireference.aspose.com/java/email/com.aspose.email/CurrentThreadSettings) para establecer la configuración regional actual. El fragmento primero establece la configuración regional a un valor no válido y luego utiliza el método [CurrentThreadSettings.setLocale](https://apireference.aspose.com/java/email/com.aspose.email/CurrentThreadSettings#setLocale\(java.lang.String\)) para establecer la configuración regional para el hilo actual.



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