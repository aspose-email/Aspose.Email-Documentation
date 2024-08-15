---
title: "Поддержка настройки локали для текущего потока"
url: /ru/java/support-for-setting-locale-for-current-thread/
weight: 50
type: docs
---

Aspose.Email предоставляет возможность установить локаль для текущего потока. Aspose.Email предоставляет класс [CurrentThreadSettings](https://apireference.aspose.com/java/email/com.aspose.email/CurrentThreadSettings) который обеспечивает [setLocale](https://apireference.aspose.com/java/email/com.aspose.email/CurrentThreadSettings#setLocale\(java.util.Locale\)) метод для этой цели. Следующий фрагмент кода демонстрирует использование [CurrentThreadSettings](https://apireference.aspose.com/java/email/com.aspose.email/CurrentThreadSettings) класс для установки текущей локали. Во фрагменте кода сначала задается неверное значение Locale, а затем используется [CurrentThreadSettings.setLocale](https://apireference.aspose.com/java/email/com.aspose.email/CurrentThreadSettings#setLocale\(java.lang.String\)) метод установки локали для текущего потока.



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