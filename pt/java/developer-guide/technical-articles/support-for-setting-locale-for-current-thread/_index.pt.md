---
title: "Suporte para definir o Local para a Thread Atual"
url: /pt/java/support-for-setting-locale-for-current-thread/
weight: 50
type: docs
---

Aspose.Email fornece a capacidade de definir o Local para a thread atual. Aspose.Email fornece uma classe [CurrentThreadSettings](https://apireference.aspose.com/java/email/com.aspose.email/CurrentThreadSettings) que oferece o método [setLocale](https://apireference.aspose.com/java/email/com.aspose.email/CurrentThreadSettings#setLocale\(java.util.Locale\)) para esse propósito. O seguinte trecho de código demonstra o uso da classe [CurrentThreadSettings](https://apireference.aspose.com/java/email/com.aspose.email/CurrentThreadSettings) para definir o Local atual. O snippet primeiro define o Local como um valor inválido e então usa o método [CurrentThreadSettings.setLocale](https://apireference.aspose.com/java/email/com.aspose.email/CurrentThreadSettings#setLocale\(java.lang.String\)) para definir o Local para a thread atual.

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