---
title: "Installation"
url: /ru/androidjava/installation/
weight: 50
type: docs
---

## **Установите Aspose.Email для Android через Java из репозитория Maven**
1. Добавьте репозиторий maven в свой build.gradle
1. Добавьте JAR «Aspose.Email для Android через Java» в качестве зависимости

~~~Java

// 1. Добавьте репозиторий maven в свой build.gradle

repositories {

    mavenCentral()

    maven { url "http://repository.aspose.com/repo/" }

}



// 2. Добавьте JAR «Aspose.Email для Android через Java» в качестве зависимости

dependencies {

    ...

    ...

    compile (

		group: 'com.aspose',

		name: 'aspose-email',

		version: '18.4',

		classifier: 'android.via.java'

	)

}

~~~
