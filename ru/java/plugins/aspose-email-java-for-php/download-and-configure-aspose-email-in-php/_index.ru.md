---
title: "Скачайте и настройте Aspose.Email на PHP"
url: /ru/java/download-and-configure-aspose-email-in-php/
weight: 10
type: docs
---

## **Загрузка необходимых библиотек**
Загрузите необходимые библиотеки, указанные ниже. Они необходимы для выполнения примеров Aspose.Электронная почта Java для PHP.

- **Aspose:** [Компонент Aspose.Email для компонента Java](https://downloads.aspose.com/total)
- [Мост PHP/Java](http://citylan.dl.sourceforge.net/project/php-java-bridge/Binary%20package/php-java-bridge_6.2.1/php-java-bridge_6.2.1_documentation.zip)
## **Загрузите примеры с сайтов социального программирования**
Следующие версии примеров запуска доступны для загрузки на нижеуказанных сайтах социального программирования:

-----
### **GitHub**
- **Примеры использования Aspose.Email на языке Java для PHP**
  - [Aspose.Электронная почта Java для PHP](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_Java_for_PHP)
### **CodePlex**
- **Примеры использования Aspose.Email на языке Java для PHP**
  - [Aspose.Электронная почта Java для PHP](https://archive.codeplex.com/?p=asposeemailjavaphp)
## **Как настроить исходный код на платформе Linux**
Выполните следующие простые шаги, чтобы открыть и расширить исходный код во время использования:
## **1. Установите сервер Tomcat**
Чтобы установить сервер tomcat, выполните следующую команду на консоли Linux. Это позволит успешно установить сервер tomcat.

``` actionscript3

 sudo apt-get install tomcat8

```
## **2. Загрузите и настройте PHP/JavaBridge**
Чтобы загрузить двоичные файлы PHP/JavaBridge, выполните следующую команду в консоли Linux.

``` actionscript3

  wget http://citylan.dl.sourceforge.net/project/php-java-bridge/Binary%20package/php-java-bridge_6.2.1/php-java-bridge_6.2.1_documentation.zip

```


Распакуйте двоичные файлы PHP/JavaBridge, выполнив следующую команду в консоли Linux.

``` actionscript3

  unzip -d php-java-bridge_6.2.1_documentation.zip

```


Это позволит извлечь **JavaBridge.war** файл. Скопируйте его в tomcat88 **webapps** папку, выполнив следующую команду на консоли Linux.

``` actionscript3

  sudo cp JavaBridge.war /var/lib/tomcat8/webapps/JavaBridge.war

```


При копировании tomcat8 автоматически создаст новую папку»**JavaBridge**«в **webapps**. После создания папки убедитесь, что ваш tomcat8 запущен, а затем проверьте <http://localhost:8080/JavaBridge> в браузере должна открываться стандартная страница JavaBridge.

Если появится сообщение об ошибке, установите  **FastCGI** выполнив следующую команду на консоли Linux.

``` actionscript3

  sudo apt-get install php55-cgi

```

После установки php5.5 cgi перезапустите сервер tomcat8 и проверьте <http://localhost:8080/JavaBridge> снова в браузере.

If **JAVA_HOME** отображается ошибка, затем откройте файл /etc/default/tomcat8 и раскомментируйте строку, в которой задан JAVA_HOME. Проверьте <http://localhost:8080/JavaBridge> опять же, в браузере должна быть страница с примерами PHP/JavaBridge. 
## **3. Настройте Java в Aspose.Email для примеров PHP**
Клонируйте примеры PHP, выполнив следующие команды в папке WebApps/JavaBridge. 

``` actionscript3

 $ git init&nbsp;

$ git clone [https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose_Email_Java_for_PHP]

```


## **Как настроить исходный код на платформе Windows**
Выполните следующие простые шаги для настройки Мост PHP/Java на платформе Windows

1. Установите PHP5 и настройте его как обычно
2. Установите JRE 6 (среда выполнения Java), если у вас ее еще нет. Вы можете проверить это в папке C:\Program Files и т. д. Загрузить ее можно здесь. Я использую JRE 6, поскольку он совместим с PHP Java Bridge (PJB).

3. Установите Apache Tomcat 8.0. Вы можете скачать его здесь

4.Download [JavaBridge.war](https://sourceforge.net/projects/php-java-bridge/files/Binary%20package/php-java-bridge_6.2.1/JavaBridgeTemplate621.war/download). Скопируйте этот файл в каталог tomcat webapps.
(например: `C:\Program Files\Apache Software Foundation\Tomcat 8.0\webapps` )

5. Перезапустите службу tomcat apache.

6. Перейти к <http://localhost:8080/JavaBridge/test.php> чтобы проверить, работает ли php. Здесь вы можете найти другие примеры

7. Скопируйте свой [Aspose.Электронная почта Java](https://downloads.aspose.com/total) jar-файл в `C:\Program Files\Apache Software Foundation\Tomcat 8.0\webapps\JavaBridge\WEB-INF\lib`

8. Clone [Aspose.Электронная почта Java для PHP](https://github.com/aspose-email/Aspose.Email-for-Java/tree/master/Plugins/Aspose.Email-for-Java_for_PHP) примеры внутри `C:\Program Files\Apache Software Foundation\Tomcat 8.0\webapps\` folder.

8. Скопировать папку `C:\Program Files\Apache Software Foundation\Tomcat 8.0\webapps\JavaBridge\java` в папку Aspose.Электронная почта Java для примеров PHP.

\ 10. Перезапустите службу apache tomcat и начните использовать примеры.
