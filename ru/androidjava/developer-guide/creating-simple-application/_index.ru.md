---
title: "Создание простого приложения"
url: /ru/androidjava/creating-simple-application/
weight: 10
type: docs
---

## **Как использовать Aspose.Emil для Android через Java**
В этом разделе вы узнаете, как настроить Aspose.Email для Android через Java в Android Studio IDE, предполагая, что на вашем компьютере уже установлена последняя версия Android Studio и вы также приобрели последнюю версию Aspose.Email для Android через пакет Java.

{{% alert color="primary" %}}

Если вы еще не установили Android Studio, вам необходимо сначала установить Android Studio и установить ее на свой компьютер. Последнюю версию Android Studio можно загрузить по ссылке [here ](https://developer.android.com/studio/index.html#win-bundle)в то время как подробная информация о том, как установить IDE, доступна [here](https://developer.android.com/studio/install.html).

{{% /alert %}} {{% alert color="primary" %}}

Aspose.Email для Android через пакет Java можно загрузить с [here](https://downloads.aspose.com/email/androidjava). Обратите внимание, что каждый релизный пакет Aspose.Email для Android на Java в основном состоит из 2 файлов, как описано ниже.

- aspose-email-x.x.x.jar — это основной файл библиотеки, содержащий все пространства имен из Aspose.Email для Android через Java API.
- aspose-email-x.x.x-libs.apk - это APK, содержащий сторонний файл bcprov-jdk15-146.jar, используемый для средств шифрования и дешифрования, предлагаемых Aspose.Email для Android через Java API.

{{% /alert %}}
## **Начало работы с Aspose.Электронная почта для Android через Java в Android Studio**
После загрузки Android Studio IDE нажмите «Файл» > «Создать» > «Новый проект», как показано ниже.

![todo:image_alt_text](run_examples_1.png)

Вы также можете создать новый проект на экране приветствия Android Studio, как показано ниже.

![todo:image_alt_text](run_examples_2.png)

Затем вам будет предложено указать имя приложения, домен и местоположение для хранения файлов проекта. Вы можете изменить значения по умолчанию по своему усмотрению или оставить их такими, какие они есть, и нажмите «Далее».

![todo:image_alt_text](run_examples_3.png)

На следующем шаге вам нужно указать устройство Android, на котором вы хотите разместить или запустить свое приложение. После выбора нажмите кнопку «Далее».

![todo:image_alt_text](run_examples_4.png)

Теперь вам нужно выбрать действие из предопределенного списка шаблонов. Чтобы упростить демонстрацию, мы выбрали шаблон Empty Activity, как показано ниже.

![todo:image_alt_text](run_examples_5.png)

Нажмите кнопку Готово в диалоговом окне «Настройка активности», так как мы сохраним все настройки по умолчанию без изменений.

![todo:image_alt_text](run_examples_6.png)

Как только вы нажмете кнопку «Готово» на предыдущем шаге, среда IDE начнет сборку проекта, как показано ниже. Дождитесь завершения или нажмите кнопку «Отмена».

![todo:image_alt_text](run_examples_7.png)

Теперь проект загружен в IDE, однако, возможно, вы захотите изменить представление на Project, чтобы увидеть полную иерархию файлов проекта. Чтобы изменить представление, посмотрите следующий снимок.

![todo:image_alt_text](run_examples_8.png)

После изменения вида на Project найдите и загрузите файл build.gradle в редактор и вставьте следующий фрагмент, как показано ниже.


~~~Java

 dexOptions{

    javaMaxHeapSize "4g"

}

~~~

![todo:image_alt_text](run_examples_9.png)

Далее мы добавим в проект Aspose.Email для Android через Java Jar. Ниже описаны два важных шага.

- Вручную скопируйте файл Aspose.Email для Android через Java Jar в папку\ app\ libs.
- Добавьте Aspose.Email для Android через Java Jar в виде библиотеки в модуль, как показано ниже.

![todo:image_alt_text](run_examples_10.png)

Вам будет предложено выбрать модуль, в который вы хотите добавить Aspose.Email для Java.Android Jar в качестве библиотеки. Выберите подходящий вариант и нажмите «ОК».

![todo:image_alt_text](run_examples_11.png)

Вам также необходимо добавить APK-файл в проект. Вам необходимо скопировать APK в папку\ app\ src\ main\ assets. Если у вас нет папки с ресурсами в основной папке, вы можете создать ее, щелкнув правой кнопкой мыши на главном узле в представлении проекта. Выберите «Создать» > «Папка» > «Папка ресурсов».

![todo:image_alt_text](run_examples_12.png)

После добавления APK в проект он должен быть загружен проектом. Есть 2 способа загрузить APK следующим образом.

- Загрузите APK в собственный класс приложения, используя приведенный ниже фрагмент, и зарегистрируйте собственный класс приложения в файле AndroidManifest.xml.


~~~Java

 LibsLoadHelper.loadLibs(this);

~~~

- Загрузите APK в методе onCreate в MainActivity.


~~~Java

 LibsLoadHelper.loadLibs(getApplicationContext());

~~~

Теперь мы готовы написать код. Чтобы демонстрация была понятной, мы добавили в макет виджет Button и будем обрабатывать событие нажатия кнопки следующим образом.


~~~Java

private class TestEmail extends AsyncTask<Void, String, Boolean>

{

    @Override

    protected Boolean doInBackground(Void... params)

    {

        Boolean result = false;

        try

        {

            //Create an instance of PersonalStorage

            com.aspose.email.PersonalStorage pst = com.aspose.email.PersonalStorage.create("newSample_out.pst", 0);

            //Create a folder at root of PST

            pst.getRootFolder().addSubFolder("myInbox");

            //Add message to newly created folder

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

При запуске приложения с помощью кнопки воспроизведения в интерфейсе IDE (или с помощью SHIFT+F10) эмулятор загрузит приложение, как показано ниже.

![todo:image_alt_text](run_examples_13.png)

При нажатии кнопки на эмуляторе код будет выполнен.
