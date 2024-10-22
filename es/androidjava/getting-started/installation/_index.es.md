---
title: "Instalación"
url: /es/androidjava/installation/
weight: 50
type: docs
---

## **Instalar Aspose.Email para Android a través de Java desde el Repositorio de Maven**
1. Agregar el repositorio de maven en tu build.gradle
1. Agregar el JAR 'Aspose.Email para Android a través de Java' como dependencia

~~~Java

// 1. Agregar el repositorio de maven en tu build.gradle 

repositories {

    mavenCentral()

    maven { url "http://repository.aspose.com/repo/" }

}



// 2. Agregar el JAR 'Aspose.Email para Android a través de Java' como dependencia

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