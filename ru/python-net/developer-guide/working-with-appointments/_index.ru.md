---
title: "Работа с назначениями"
url: /ru/python-net/working-with-appointments/
weight: 20
type: docs
---


## **Загрузка и сохранение встречи в формате ICS**
Класс Appointment в Aspose.Email API можно использовать для загрузки встречи в формате ICS, а также для создания новой встречи и сохранения ее на диске в формате ICS. В этой статье мы сначала создаем встречу и сохраняем ее на диске в формате ICS, а затем загружаем ее.
### **Создать встречу и сохранить на диск в формате ICS**
Чтобы создать встречу и сохранить ее в формате ICS, необходимо выполнить следующие шаги.

1. Создайте экземпляр класса Appointment и инициализируйте его с помощью этого конструктора.
1. Передайте следующие аргументы в приведенном выше конструкторе
   1. Attendees
   1. Description
   1. Дата окончания
   1. Location
   1. Organizer
   1. Дата начала
   1. Summary
1. Вызовите метод Save () и укажите имя и формат файла в аргументах.

Встречу можно открыть в Microsoft Outlook или любой программе, которая может загрузить файл ICS. Если файл открыт в Microsoft Outlook, встреча автоматически добавляется в календарь Outlook.

В следующих фрагментах кода показано, как создать и сохранить встречу на диске в формате ICS.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-CreateAppointment-CreateAppointment.py" >}}
### **Формат встречи на загрузку ICS**
Чтобы загрузить встречу в формате ICS, необходимо выполнить следующие шаги:

1. Создайте экземпляр класса Appointment.
1. Вызовите метод Load (), указав путь к файлу ICS.
1. Прочтите любой объект недвижимости, чтобы получить любую информацию о встрече (файл ICS).

В следующих фрагментах кода показано, как загрузить встречу в формате ICS.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-LoadAppointment-LoadAppointment.py" >}}
## **Чтение нескольких событий из файла ICS**
{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-ReadMultipleEventsFromICS-ReadMultipleEventsFromICS.py" >}}
## **Запись нескольких событий в файл ICS**
{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-WriteMultipleEventsToICS-WriteMultipleEventsToICS.py" >}}
## **Создайте черновик запроса на встречу**
В наших предыдущих статьях было показано, как создать и сохранить встречу в формате ICS. Часто требуется создать заявку на прием в черновом режиме, чтобы добавить основную информацию, а затем отправить тот же черновик встречи другим пользователям для внесения необходимых изменений в соответствии с пожеланиями отдельных пользователей. Чтобы сохранить запись на собеседование в черновом режиме, **Method** для свойства класса Appointment должно быть установлено значение **Publish**. В следующем фрагменте кода показано, как создать черновик запроса на встречу.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-DraftAppointmentRequest-DraftAppointmentRequest.py" >}}
### **Создание проекта встречи на основе текста**
В следующем фрагменте кода показано, как создать черновик встречи из текста. 

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-CreateAppointmentFromString-CreateAppointmentFromString.py" >}}
## **Установите статус участников для участников встречи**
Aspose.Email for .NET API позволяет задавать статус участников встречи при составлении ответного сообщения. Это добавляет свойство PARTSTAT в файл ICS.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithAppointments-SetParticipantStatusOfAppointmentAttendees-SetParticipantStatusOfAppointmentAttendees.py" >}}
