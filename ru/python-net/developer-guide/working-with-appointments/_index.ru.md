---
title: "Работа с Встречами"
url: /ru/python-net/working-with-appointments/
weight: 20
type: docs
---


## **Загрузка и Сохранение Встречи в Формате ICS**
Класс Appointment в Aspose.Email API может быть использован для загрузки встречи в формате ICS, а также для создания новой встречи и сохранения её на диск в формате ICS. В этой статье мы сначала создадим встречу и сохраним её на диск в формате ICS, а затем мы загрузим её.
### **Создание Встречи и Сохранение на Диск в Формате ICS**
Для создания встречи и сохранения её в формате ICS необходимо выполнить следующие шаги.

1. Создайте экземпляр класса Appointment и инициализируйте его с помощью этого конструктора.
1. Передайте следующие аргументы в вышеприведённый конструктор:
   1. Участники
   1. Описание
   1. Дата окончания
   1. Место
   1. Организатор
   1. Дата начала
   1. Резюме
1. Вызовите метод Save() и укажите имя файла и формат в аргументах.

Встречу можно открыть в Microsoft Outlook или в любой программе, которая может загрузить файл ICS. Если файл открыт в Microsoft Outlook, он автоматически добавляет встречу в календарь Outlook.

Следующий код показывает, как создать и сохранить встречу на диск в формате ICS.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-CreateAppointment-CreateAppointment.py" >}}
### **Загрузка Встречи в Формате ICS**
Для загрузки встречи в формате ICS необходимо выполнить следующие шаги:

1. Создайте экземпляр класса Appointment.
1. Вызовите метод Load(), указав путь к файлу ICS.
1. Считайте любое свойство, чтобы получить информацию о встрече (файл ICS).

Следующий код показывает, как загрузить встречу в формате ICS.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-LoadAppointment-LoadAppointment.py" >}}
## **Чтение Нескольких Событий из Файла ICS**
{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-ReadMultipleEventsFromICS-ReadMultipleEventsFromICS.py" >}}
## **Запись Нескольких Событий в Файл ICS**
{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-WriteMultipleEventsToICS-WriteMultipleEventsToICS.py" >}}
## **Создание Запроса на Встречу в Черновике**
В наших предыдущих статьях было показано, как создать и сохранить встречу в формате ICS. Часто требуется создать запрос на встречу в режиме черновика, чтобы основная информация была добавлена, а затем этот черновик встречи был перенаправлен другим пользователям для необходимых изменений в соответствии с индивидуальными пользователями. Чтобы сохранить встречу в режиме черновика, свойство **Method** класса Appointment должно быть установлено в **Publish**. Следующий код показывает, как создать запрос на встречу в черновике.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-DraftAppointmentRequest-DraftAppointmentRequest.py" >}}
### **Создание Черновика Встречи из Текста**
Следующий код показывает, как создать черновик встречи из текста. 

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-CreateAppointmentFromString-CreateAppointmentFromString.py" >}}
## **Установить Статус Участников Встречи**
Aspose.Email для .NET API позволяет установить статус участников встречи во время составления ответного сообщения. Это добавляет свойство PARTSTAT в файл ICS.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-SetParticipantStatusOfAppointmentAttendees-SetParticipantStatusOfAppointmentAttendees.py" >}}