---
title: "Загрузка и настройка Aspose.Email в PHP"
url: /ru/java/download-and-configure-aspose-email-in-php/
weight: 10
type: docs
---

## **Скачайте необходимые библиотеки**
Скачайте необходимые библиотеки, упомянутые ниже. Они необходимы для выполнения примеров Aspose.Email для PHP.

- **Aspose:** [Aspose.Email для Java компонент](https://downloads.aspose.com/total)
- [PHP/Java Bridge](http://citylan.dl.sourceforge.net/project/php-java-bridge/Binary%20package/php-java-bridge_6.2.1/php-java-bridge_6.2.1_documentation.zip)
## **Скачайте примеры с сайтов социального кодирования**
Следующие выпуски работающих примеров доступны для скачивания на упомянутых ниже социальных сайтах:

-----
### **GitHub**
- **Примеры Aspose.Email Java для PHP**
  - [Aspose.Email Java для PHP](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_Java_for_PHP)
### **CodePlex**
- **Примеры Aspose.Email Java для PHP**
  - [Aspose.Email Java для PHP](https://archive.codeplex.com/?p=asposeemailjavaphp)
## **Как настроить исходный код на платформе Linux**
Пожалуйста, выполните следующие простые шаги, чтобы открыть и расширить исходный код, используя:
## **1. Установите сервер Tomcat**
Чтобы установить сервер tomcat, выполните следующую команду в консоли linux. Это успешно установит сервер tomcat.

``` actionscript3

 sudo apt-get install tomcat8

```
## **2. Скачайте и настройте PHP/JavaBridge**
Чтобы скачать исполняемые файлы PHP/JavaBridge, выполните следующую команду в консоли linux.

``` actionscript3

  wget http://citylan.dl.sourceforge.net/project/php-java-bridge/Binary%20package/php-java-bridge_6.2.1/php-java-bridge_6.2.1_documentation.zip 

```

Распакуйте исполняемые файлы PHP/JavaBridge, выполнив следующую команду в консоли linux.

``` actionscript3

  unzip -d php-java-bridge_6.2.1_documentation.zip 

```

Это извлечет файл **JavaBridge.war**. Скопируйте его в папку tomcat88 **webapps**, выполнив следующую команду в консоли Linux.

``` actionscript3

  sudo cp JavaBridge.war /var/lib/tomcat8/webapps/JavaBridge.war 

```

При копировании tomcat8 автоматически создаст новую папку "**JavaBridge**" в **webapps**. После создания папки убедитесь, что ваш tomcat8 запущен, а затем проверьте <http://localhost:8080/JavaBridge> в браузере, он должен открыть страницу по умолчанию JavaBridge.

Если появляется сообщение об ошибке, установите **FastCGI**, выполнив следующую команду в консоли Linux.

``` actionscript3

  sudo apt-get install php55-cgi 

```

После установки php5.5 cgi перезапустите сервер tomcat8 и снова проверьте <http://localhost:8080/JavaBridge> в браузере.

Если отображается ошибка **JAVA_HOME**, откройте файл /etc/default/tomcat8 и раскомментируйте строку, устанавливающую JAVA_HOME. Проверьте <http://localhost:8080/JavaBridge> в браузере снова, это должно привести к странице примеров PHP/JavaBridge. 
## **3. Настройка примеров Aspose.Email Java для PHP**
Клонируйте примеры PHP, выполнив следующие команды внутри папки webapps/JavaBridge. 

``` actionscript3

 $ git init&nbsp;

$ git clone [https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_Java_for_PHP] 

```

## **Как настроить исходный код на платформе Windows**
Пожалуйста, выполните следующие простые шаги для настройки PHP/Java Bridge на платформе Windows

1. Установите PHP5 и настройте его, как обычно
2. Установите JRE 6 (Java Runtime Environment), если у вас его еще нет. Вы можете проверить это в C:\Program Files и т. д. Вы можете скачать его здесь. Я использую JRE 6, поскольку он совместим с PHP Java Bridge (PJB).

3. Установите Apache Tomcat 8.0. Вы можете скачать его здесь

4. Скачать [JavaBridge.war](https://sourceforge.net/projects/php-java-bridge/files/Binary%20package/php-java-bridge_6.2.1/JavaBridgeTemplate621.war/download). Скопируйте этот файл в директорию webapps tomcat.
(например: `C:\Program Files\Apache Software Foundation\Tomcat 8.0\webapps` )

5. Перезапустите службу apache tomcat.

6. Перейдите на <http://localhost:8080/JavaBridge/test.php>, чтобы проверить, работает ли php. Вы можете найти другие примеры там.

7. Скопируйте ваш [Aspose.Email Java](https://downloads.aspose.com/total) jar файл в `C:\Program Files\Apache Software Foundation\Tomcat 8.0\webapps\JavaBridge\WEB-INF\lib`

8. Клонируйте [Aspose.Email Java для PHP](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose.Email-for-Java_for_PHP) примеры внутри папки `C:\Program Files\Apache Software Foundation\Tomcat 8.0\webapps\`.

9. Скопируйте папку `C:\Program Files\Apache Software Foundation\Tomcat 8.0\webapps\JavaBridge\java` в папку ваших примеров Aspose.Email Java для PHP.

10. Перезапустите службу apache tomcat и начните использовать примеры.