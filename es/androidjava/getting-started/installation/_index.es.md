---
title: "Installation"
url: /es/androidjava/installation/
weight: 50
type: docs
---

## **Instale Aspose.Email para Android a través de Java desde Maven Repository**
1. Agrega el repositorio maven a tu build.gradle
1. Agregue el JAR 'Aspose.Email para Android a través de Java' como dependencia

~~~Java

// 1. Agrega el repositorio maven a tu build.gradle

repositories {

    mavenCentral()

    maven { url "http://repository.aspose.com/repo/" }

}



// 2. Agregue el JAR 'Aspose.Email para Android a través de Java' como dependencia

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
