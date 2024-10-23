---
title: "Instalação"
url: /pt/androidjava/installation/
weight: 50
type: docs
---

## **Instalar Aspose.Email para Android via Java a partir do Repositório Maven**
1. Adicione o repositório maven ao seu build.gradle
1. Adicione o JAR 'Aspose.Email para Android via Java' como uma dependência

~~~Java

// 1. Adicione o repositório maven ao seu build.gradle 

repositories {

    mavenCentral()

    maven { url "http://repository.aspose.com/repo/" }

}



// 2. Adicione o JAR 'Aspose.Email para Android via Java' como uma dependência

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