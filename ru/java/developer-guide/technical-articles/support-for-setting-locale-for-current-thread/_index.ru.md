---
title: "Поддержка установки Locale для текущего потока"
url: /ru/java/support-for-setting-locale-for-current-thread/
weight: 50
type: docs
---

Aspose.Email предоставляет возможность установить Locale для текущего потока. Aspose.Email предоставляет класс [CurrentThreadSettings](https://apireference.aspose.com/java/email/com.aspose.email/CurrentThreadSettings), который предоставляет метод [setLocale](https://apireference.aspose.com/java/email/com.aspose.email/CurrentThreadSettings#setLocale\(java.util.Locale\)) для этой цели. Следующий фрагмент кода демонстрирует использование класса [CurrentThreadSettings](https://apireference.aspose.com/java/email/com.aspose.email/CurrentThreadSettings) для установки текущего Locale. Сначала фрагмент устанавливает Locale на недопустимое значение, а затем использует метод [CurrentThreadSettings.setLocale](https://apireference.aspose.com/java/email/com.aspose.email/CurrentThreadSettings#setLocale\(java.lang.String\)) для установки Locale для текущего потока.

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