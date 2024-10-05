---
title: "Создание Простого Приложения"
url: /ru/androidjava/creating-simple-application/
weight: 10
type: docs
---

## **Как использовать Aspose.Email для Android через Java**
Этот раздел проведет вас через необходимые шаги по настройке Aspose.Email для Android через Java в среде разработки Android Studio, предполагая, что у вас уже установлена последняя версия Android Studio на вашем компьютере и вы также получили последнюю версию пакета Aspose.Email для Android через Java.

{{% alert color="primary" %}} 

Если вы еще не установили Android Studio, сначала вам необходимо скачать установочный файл Android Studio и установить его на вашем компьютере. Вы можете загрузить последнюю версию Android Studio [здесь](https://developer.android.com/studio/index.html#win-bundle), тогда как детали о том, как установить IDE, доступны [здесь](https://developer.android.com/studio/install.html).

{{% /alert %}} {{% alert color="primary" %}} 

Пакет Aspose.Email для Android через Java можно загрузить [здесь](https://downloads.aspose.com/email/androidjava). Обратите внимание, что каждый релиз пакета Aspose.Email для Android через Java в основном состоит из 2 файлов, как указано ниже.

- aspose-email-x.x.x.jar — это основной файл библиотеки, содержащий все пространства имен из API Aspose.Email для Android через Java.
- aspose-email-x.x.x-libs.apk — это APK, содержащий сторонний файл bcprov-jdk15-146.jar, используемый для инструментов шифрования и расшифровки, предлагаемых API Aspose.Email для Android через Java.

{{% /alert %}} 
## **Начало работы с Aspose.Email для Android через Java в Android Studio**
Как только IDE Android Studio загрузится, нажмите Файл > Новый > Новый проект, как показано ниже.

![todo:image_alt_text](run_examples_1.png)

Вы также можете создать новый проект с экрана приветствия Android Studio, как показано ниже.

![todo:image_alt_text](run_examples_2.png)

Далее вам будет предложено указать имя приложения, домен и местоположение для сохранения файлов проекта. Вы можете выбрать изменение значений по умолчанию на ваше усмотрение или оставить их как есть, и нажать Далее.

![todo:image_alt_text](run_examples_3.png)

На следующем шаге вам нужно указать устройство Android, на котором вы хотите запустить ваше приложение. После выбора нажмите кнопку Далее.

![todo:image_alt_text](run_examples_4.png)

Теперь вам нужно выбрать Activity из заранее определенного списка шаблонов. Чтобы сделать демонстрацию простой, мы выбрали шаблон Пустая Activity, как показано ниже.

![todo:image_alt_text](run_examples_5.png)

Нажмите кнопку Завершить в диалоговом окне Настройка Activity, так как мы оставим все настройки по умолчанию.

![todo:image_alt_text](run_examples_6.png)

Как только вы нажмете кнопку Завершить на предыдущем шаге, IDE начнет собирать проект, как показано ниже. Позвольте процессу завершиться или нажмите кнопку Отмена.

![todo:image_alt_text](run_examples_7.png)

Теперь проект загружен в IDE, однако вы можете изменить представление на Проект, чтобы посмотреть полную иерархию файлов проекта. Чтобы изменить представление, посмотрите на следующий снимок.

![todo:image_alt_text](run_examples_8.png)

После изменения представления на Проект найдите и откройте файл build.gradle в редакторе и вставьте следующий фрагмент, как показано ниже.

~~~Java

 dexOptions{

    javaMaxHeapSize "4g"

}

~~~

![todo:image_alt_text](run_examples_9.png)

Далее мы добавим JAR Aspose.Email для Android через Java в проект. Есть 2 важных шага, как указано ниже.

- Вручную скопируйте JAR Aspose.Email для Android через Java в папку \app\libs.
- Добавьте JAR Aspose.Email для Android через Java в качестве библиотеки к модулю, как показано ниже.

![todo:image_alt_text](run_examples_10.png)

Вам будет предложено выбрать модуль, в который вы хотите добавить JAR Aspose.Email для Java.Android в качестве библиотеки. Пожалуйста, выберите соответствующий и нажмите ОК.

![todo:image_alt_text](run_examples_11.png)

Вам также нужно добавить APK файл в проект. Вы должны скопировать APK в папку \app\src\main\assets. Если у вас нет папки assets в главной папке, вы можете создать ее, щелкнув правой кнопкой мыши по главному узлу в представлении проекта. Выберите Новый > Папка > Папка ресурсов.

![todo:image_alt_text](run_examples_12.png)

После того как APK добавлен в проект, его необходимо загрузить проектом. Есть 2 способа загрузить APK следующим образом.

- Загрузите APK в пользовательском классе приложения, используя приведенный ниже фрагмент, и зарегистрируйте пользовательский класс приложения в AndroidManifest.xml.

~~~Java

 LibsLoadHelper.loadLibs(this);

~~~

- Загрузите APK в методе OnCreate MainActivity.

~~~Java

 LibsLoadHelper.loadLibs(getApplicationContext());

~~~

Теперь мы готовы написать код. Чтобы сделать демонстрацию легкой для понимания, мы добавили виджет Кнопка в макет и собираемся обработать его событие нажатия следующим образом.

~~~Java

private class TestEmail extends AsyncTask<Void, String, Boolean> 

{

    @Override

    protected Boolean doInBackground(Void... params) 

    {

        Boolean result = false;

        try 

        {

            //Создать экземпляр PersonalStorage

            com.aspose.email.PersonalStorage pst = com.aspose.email.PersonalStorage.create("newSample_out.pst", 0);

            //Создать папку в корне PST

            pst.getRootFolder().addSubFolder("myInbox");

            //Добавить сообщение в вновь созданную папку

            pst.getRootFolder().getSubFolder("myInbox").addMessage(com.aspose.email.MapiMessage.fromFile("message.msg"));

        } 

        catch (Exception e) 

        {

            e.printStackTrace();

        }

        return result;

    }

}

~~~

Когда вы запустите приложение, используя кнопку воспроизведения в интерфейсе IDE (или используя SHIFT + F10), эмулятор загрузит приложение, как показано ниже.

![todo:image_alt_text](run_examples_13.png)

Нажатие на кнопку в эмуляторе выполнит код.