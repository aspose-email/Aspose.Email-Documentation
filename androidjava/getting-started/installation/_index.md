---
title: Installation
type: docs
weight: 50
url: /androidjava/installation/
---

## **Install Aspose.Email for Android via Java from Maven Repository**
1. Add maven repository into your build.gradle
1. Add 'Aspose.Email for Android via Java' JAR as a dependency

~~~Java

// 1. Add maven repository into your build.gradle 

repositories {

    mavenCentral()

    maven { url "http://repository.aspose.com/repo/" }

}



// 2. Add 'Aspose.Email for Android via Java' JAR as a dependency

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
