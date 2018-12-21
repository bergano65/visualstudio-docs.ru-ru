---
title: Оптимизация кода Azure в Visual Studio | Документация Майкрософт
description: Узнайте о том, как Azure кода средства оптимизации в Visual Studio помогут сделать код более надежным и производительным.
author: ghogen
manager: douge
ms.assetid: ed48ee06-e2d2-4322-af22-07200fb16987
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: ghogen
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: d1d0f5a69015a6c6596e1a2b7ee85b12f4116d6b
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002517"
---
# <a name="optimizing-your-azure-code"></a>Оптимизация кода Azure
При программировании приложений, использующих Microsoft Azure, существуют определенные принципы программирования, следует придерживаться, чтобы избежать проблем с масштабированием, поведение и производительность в облачной среде. Корпорация Майкрософт предоставляет средство анализа кода Azure, который распознает и идентифицирует эти часто встречающиеся проблемы, а также помогает их решить. Можно загрузить средство в Visual Studio с помощью NuGet.

## <a name="azure-code-analysis-rules"></a>Правила анализа кода Azure
Средство анализа кода Azure использует следующие правила для автоматически помечает соответствующий код Azure, когда обнаруживает известные проблемы, влияющие на производительность. Обнаруженные проблемы отображаются в виде предупреждений или ошибок компилятора. Средства исправления кода или предложения, чтобы устранить предупреждения или ошибки часто предоставляются через значок лампочки.

## <a name="avoid-using-default-in-process-session-state-mode"></a>Старайтесь не использовать режим состояния сеанса (в процессе) по умолчанию
### <a name="id"></a>ID
AP0000

### <a name="description"></a>Описание
Если вы используете режим состояния сеанса (в процессе) по умолчанию для облачных приложений, вы можете потерять состояние сеанса.

Поделитесь своими идеями и предложениями на [отзывов об анализе кода Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Причина
По умолчанию указанные в файле web.config режима состояния сеанса в процессе. Кроме того Если нет соответствующей записи в файле конфигурации, режимом состояния сеанса по умолчанию в процессе. Внутрипроцессный режим хранит состояние сеанса в памяти на веб-сервере. При перезапуске экземпляра или экземпляра используется для балансировки нагрузки и отработки отказа, не сохраняется состояние сеанса, хранимое в памяти на веб-сервере. Такая ситуация не позволяет приложению быть масштабируемым в облаке.

Состояние сеанса ASP.NET поддерживает несколько различных параметров хранения данных о состоянии сеанса: InProc, StateServer, SQLServer, Custom и Off. Рекомендуется использовать пользовательский режим для размещения данных на внешнем хранилище состояния сеанса, таких как [поставщик состояния сеанса Azure для Redis](http://go.microsoft.com/fwlink/?LinkId=401521).

### <a name="solution"></a>Решение
Одно из рекомендуемых решений — хранение состояния сеанса на управляемая служба кэша. Сведения об использовании [поставщик состояния сеанса Azure для Redis](http://go.microsoft.com/fwlink/?LinkId=401521) для хранения состояния сеанса. Можно также хранить состояние сеанса в других местах, чтобы убедиться, что приложение является масштабируемой в облаке. Дополнительные сведения об альтернативных решениях см. в статье [режимы состояний сеанса](https://msdn.microsoft.com/library/ms178586).

## <a name="run-method-should-not-be-async"></a>Метод Run не должен быть асинхронным
### <a name="id"></a>ID
AP1000

### <a name="description"></a>Описание
Создайте асинхронные методы (такие как [await](https://msdn.microsoft.com/library/hh156528.aspx)) за пределами [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) метода и затем вызывать эти методы из [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx). Объявление [ [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) метод асинхронным приводит рабочей роли в цикл перезагрузки.

Поделитесь своими идеями и предложениями на [отзывов об анализе кода Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Причина
Вызов асинхронных методов в [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) метод вызывает среду выполнения облачной службы к перезапуску рабочей роли. При запуске рабочей роли все выполнение программы происходит в [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) метод. Выход из [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) метод приводит к перезапуску рабочей роли. Когда среда выполнения рабочей роли сталкивается с асинхронным методом, она производит диспетчеризацию всех операций после асинхронного метода и возвращает. Это приводит к рабочей роли для выхода из [ [ [ [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) метод и перезапуска. В следующей итерации выполнения рабочая роль снова попадает на асинхронный метод и перезапускается, приводит к ее снова, а также перезапуск.

### <a name="solution"></a>Решение
Разместите все асинхронные операции вне [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) метод. Затем вызовите рефакторизованный асинхронный метод из [ [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) метода, например RunAsync () .wait. Средство анализа кода Azure может помочь устранить эту проблему.

В следующем фрагменте кода демонстрируется код исправления этой проблемы:

```
public override void Run()
{
    RunAsync().Wait();
}

public async Task RunAsync()
{
    //Asynchronous operations code logic
    // This is a sample worker implementation. Replace with your logic.

    Trace.TraceInformation("WorkerRole1 entry point called");

    HttpClient client = new HttpClient();

    Task<string> urlString = client.GetStringAsync("http://msdn.microsoft.com");

    while (true)
    {
        Thread.Sleep(10000);
        Trace.TraceInformation("Working");

        string stream = await urlString;
    }

}
```

## <a name="use-service-bus-shared-access-signature-authentication"></a>Использовать проверку подлинности подписи общего доступа Service Bus
### <a name="id"></a>ID
AP2000

### <a name="description"></a>Описание
Использование подписи общего доступа (SAS) для проверки подлинности. Не будет использоваться служба контроля доступа (ACS) для проверки подлинности служебной шины.

Поделитесь своими идеями и предложениями на [отзывов об анализе кода Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Причина
Для повышения уровня безопасности Azure Active Directory заменяет проверку подлинности ACS с помощью проверки подлинности SAS. См. в разделе [Azure Active Directory — это будущее ACS](https://cloudblogs.microsoft.com/enterprisemobility/2013/06/22/azure-active-directory-is-the-future-of-acs/) сведения о плане перехода.

### <a name="solution"></a>Решение
Использование проверки подлинности SAS в приложениях. Приведенный ниже показано, как использовать существующий маркер SAS для доступа к пространству имен служебной шины или сущности.

```
MessagingFactory listenMF = MessagingFactory.Create(endpoints, new StaticSASTokenProvider(subscriptionToken));
SubscriptionClient sc = listenMF.CreateSubscriptionClient(topicPath, subscriptionName);
BrokeredMessage receivedMessage = sc.Receive();
```

Дополнительные сведения см.

* Дополнительные сведения см. в разделе [общего доступа подпись проверки подлинности с помощью служебной шины](https://msdn.microsoft.com/library/dn170477.aspx)
* [Как использовать проверка подлинности подписи общего доступа с помощью служебной шины](https://msdn.microsoft.com/library/dn205161.aspx)
* Пример проекта, см. в разделе [проверки подлинности с помощью общих подписи доступа (SAS) с подписками Service Bus](http://code.msdn.microsoft.com/windowsazure/Using-Shared-Access-e605b37c)

## <a name="consider-using-onmessage-method-to-avoid-receive-loop"></a>Рекомендуется использовать метод OnMessage, чтобы избежать «цикла получения»
### <a name="id"></a>ID
AP2002

### <a name="description"></a>Описание
Чтобы избежать вхождения в «цикл получения,» вызова **OnMessage** является лучшим решением для получения сообщений, чем вызов в метод **Receive** метод. Тем не менее если необходимо использовать **Receive** метод и задать время ожидания сервера не по умолчанию, убедитесь, что время ожидания сервера превышает одну минуту.

Поделитесь своими идеями и предложениями на [отзывов об анализе кода Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Причина
При вызове **OnMessage**, клиент начинает процесс обработки внутренних сообщений, который постоянно опрашивает очередь или подписку. Этот процесс обработки сообщений содержит бесконечный цикл, который отправляет вызов для получения сообщений. Если время ожидания вызова истекает, она выдает новый вызов. Интервал времени ожидания определяется по значению [OperationTimeout](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactorysettings.operationtimeout.aspx) свойство [MessagingFactory](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactory.aspx), который используется.

Преимущество использования **OnMessage** по сравнению с **Receive** пользователей не требуется вручную извлекать сообщения, обрабатывать исключения, обрабатывать несколько сообщений в параллельном режиме и завершать сообщения.

При вызове метода **Receive** без использования значения по умолчанию, убедитесь, что *ServerWaitTime* значение — более одной минуты. Установка *ServerWaitTime* более одной минуты предотвращает сервером истекает время ожидания до полного получения сообщения.

### <a name="solution"></a>Решение
См. в следующих примерах кода, рекомендованного использования. Дополнительные сведения см. в разделе [метод QueueClient.OnMessage (Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.onmessage.aspx)и [метод QueueClient.Receive (Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.receive.aspx).

Для повышения производительности инфраструктуры обмена сообщениями Azure ознакомьтесь с конструктивным шаблоном [асинхронному обмену сообщениями](https://msdn.microsoft.com/library/dn589781.aspx).

Ниже приведен пример использования **OnMessage** для получения сообщений.

```
void ReceiveMessages()
{
    // Initialize message pump options.
    OnMessageOptions options = new OnMessageOptions();
    options.AutoComplete = true; // Indicates if the message-pump should call complete on messages after the callback has completed processing.
    options.MaxConcurrentCalls = 1; // Indicates the maximum number of concurrent calls to the callback the pump should initiate.
    options.ExceptionReceived += LogErrors; // Enables you to get notified of any errors encountered by the message pump.

    // Start receiving messages.
    QueueClient client = QueueClient.Create("myQueue");
    client.OnMessage((receivedMessage) => // Initiates the message pump and callback is invoked for each message that is recieved, calling close on the client will stop the pump.
    {
        // Process the message.
    }, options);
    Console.WriteLine("Press any key to exit.");
    Console.ReadKey();
```

Ниже приведен пример использования **Receive** с временем ожидания сервера по умолчанию.

```
string connectionString =  
CloudConfigurationManager.GetSetting("Microsoft.ServiceBus.ConnectionString");

QueueClient Client =  
    QueueClient.CreateFromConnectionString(connectionString, "TestQueue");

while (true)  
{   
   BrokeredMessage message = Client.Receive();
   if (message != null)
   {
      try  
      {
         Console.WriteLine("Body: " + message.GetBody<string>());
         Console.WriteLine("MessageID: " + message.MessageId);
         Console.WriteLine("Test Property: " +  
            message.Properties["TestProperty"]);

         // Remove message from queue
         message.Complete();
      }

      catch (Exception)
      {
         // Indicate a problem, unlock message in queue
         message.Abandon();
      }
   }
```

Ниже приведен пример использования **Receive** с временем ожидания сервера не по умолчанию.

```
while (true)  
{   
   BrokeredMessage message = Client.Receive(new TimeSpan(0,1,0));

   if (message != null)
   {
      try  
      {
         Console.WriteLine("Body: " + message.GetBody<string>());
         Console.WriteLine("MessageID: " + message.MessageId);
         Console.WriteLine("Test Property: " +  
            message.Properties["TestProperty"]);

         // Remove message from queue
         message.Complete();
      }

      catch (Exception)
      {
         // Indicate a problem, unlock message in queue
         message.Abandon();
      }
   }
}
```
## <a name="consider-using-asynchronous-service-bus-methods"></a>Рассмотрите возможность использования асинхронных методов служебной шины
### <a name="id"></a>ID
AP2003

### <a name="description"></a>Описание
Используйте асинхронные методы служебной шины для повышения производительности обмена сообщениями через посредника.

Поделитесь своими идеями и предложениями на [отзывов об анализе кода Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Причина
Использование асинхронных методов обеспечивает программный параллелизм приложений, так как выполнение каждого вызова не блокирует основной поток. При использовании служебной шины методов обмена сообщениями, выполняя операцию (отправки, получения, удаления, и т.д.) занимает время. Это время входит обработка операции службой Service Bus, а также задержка запроса и ответа. Чтобы увеличить количество операций в единицу времени, необходимо выполнять их параллельно. Дополнительные сведения см. в [советы и рекомендации по производительности улучшения с помощью обмене сообщениями служебной шины](https://msdn.microsoft.com/library/azure/hh528527.aspx).

### <a name="solution"></a>Решение
См. в разделе [класс QueueClient (Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.aspx) сведения о способах использования рекомендованного асинхронного метода.

Для повышения производительности инфраструктуры обмена сообщениями Azure ознакомьтесь с конструктивным шаблоном [асинхронному обмену сообщениями](https://msdn.microsoft.com/library/dn589781.aspx).

## <a name="consider-partitioning-service-bus-queues-and-topics"></a>Рассмотрите возможность секционирования очереди служебной шины и разделы
### <a name="id"></a>ID
AP2004

### <a name="description"></a>Описание
Раздел служебной шины очереди и разделы для повышения производительности обмена сообщениями служебной шины.

Поделитесь своими идеями и предложениями на [отзывов об анализе кода Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Причина
Секционирование очередей и разделов шины службы повышает доступность пропускной способности и службе производительности, поскольку общая пропускная способность секционированной очереди или раздела больше не ограничивается производительностью одного брокера сообщений или хранилища сообщений. Кроме того при возникновении временного сбоя хранилища сообщений не делает в секционированную очередь или раздел недоступен. Дополнительные сведения см. в разделе [секционирование сущностей обмена сообщениями](https://msdn.microsoft.com/library/azure/dn520246.aspx).

### <a name="solution"></a>Решение
В следующем фрагменте кода показано, как секционирование сущностей обмена сообщениями.

```
// Create partitioned topic.
NamespaceManager ns = NamespaceManager.CreateFromConnectionString(myConnectionString);
TopicDescription td = new TopicDescription(TopicName);
td.EnablePartitioning = true;
ns.CreateTopic(td);
```

Дополнительные сведения см. в разделе [секционированных очередей служебной шины и разделы | Блог Microsoft Azure](https://azure.microsoft.com/blog/2013/10/29/partitioned-service-bus-queues-and-topics/) и извлечь [Microsoft Azure Service Bus секционированной очереди](https://code.msdn.microsoft.com/windowsazure/Service-Bus-Partitioned-7dfd3f1f) образца.

## <a name="do-not-set-sharedaccessstarttime"></a>Не задавайте значение SharedAccessStartTime
### <a name="id"></a>ID
AP3001

### <a name="description"></a>Описание
Следует избегать, для параметра sharedaccessstarttime текущее время немедленно запустить политику общего доступа. Необходимо задать это свойство, если вы хотите запустить политику общего доступа в дальнейшем.

Поделитесь своими идеями и предложениями на [отзывов об анализе кода Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Причина
Синхронизация часов вызывает небольшую разницу во времени между центрами обработки данных. Например можно логически было бы подумать, указать время запуска политики SAS хранилища на текущее время с помощью DateTime.Now или аналогичного метода приведет к политики SAS вступают в силу немедленно. Однако небольшая разница во времени между центрами обработки данных может вызвать проблемы с этим, так как иногда центра обработки данных будут немного отставать от времени запуска, а другие — опережать. Таким образом, истекает политики SAS может быстро (или даже немедленно) Если слишком короткое время жизни политики.

Дополнительные рекомендации по использованию подписи общего доступа в службе хранилища Azure, см. в разделе [Знакомство с SAS таблиц (подпись общего доступа), SAS очередей и обновления в SAS BLOB-объектов — блог группы хранилища Microsoft Azure — сайта Главная — блоги MSDN](http://blogs.msdn.com/b/windowsazurestorage/archive/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas.aspx).

### <a name="solution"></a>Решение
Удалите оператор, который задает время запуска политики общего доступа. Средство анализа кода Azure предоставляет исправление этой проблемы. Дополнительные сведения об управлении безопасностью см. в шаблоне разработки [шаблон ключа Камердинера](https://msdn.microsoft.com/library/dn568102.aspx).

В следующем фрагменте кода демонстрируется код исправления этой проблемы.

```
// The shared access policy provides  
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
   SharedAccessExpiryTime = DateTime.UtcNow.AddHours(10),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

## <a name="shared-access-policy-expiry-time-must-be-more-than-five-minutes"></a>Общей политики доступа, время окончания срока действия должно быть более чем за пять минут
### <a name="id"></a>ID
AP3002

### <a name="description"></a>Описание
Может быть настолько, насколько до пяти минут разница в часах между центрами обработки данных в разных местах, из-за условия, известного как «разницы в показаниях часов.» Во избежание SAS маркер политики не истекает раньше, чем планировалось, установите время быть более чем за пять минут.

Поделитесь своими идеями и предложениями на [отзывов об анализе кода Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Причина
Центры обработки данных в разных местах по всему миру синхронизировать по сигналу часов. Поскольку занять некоторое время передача в разные расположения сигнала, несмотря на то, что теоретически все синхронизировано может быть разница во времени между центрами обработки данных в разных географических местоположениях. Разница во времени может повлиять на общего доступа интервал времени и истечения срока действия в запуска политики. Таким образом чтобы убедиться, что политику общего доступа вступает в силу немедленно, не указывайте время начала. Кроме того убедитесь, что срок действия составляет более 5 минут, чтобы предотвратить раннее истечение времени ожидания.

Дополнительные сведения об использовании подписи общего доступа в службе хранилища Azure см. в разделе [Знакомство с SAS таблиц (подпись общего доступа), SAS очередей и обновления в SAS BLOB-объектов — блог группы хранилища Microsoft Azure — сайта Главная — блоги MSDN](http://blogs.msdn.com/b/windowsazurestorage/archive/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas.aspx).

### <a name="solution"></a>Решение
Дополнительные сведения об управлении безопасностью см. в шаблоне разработки [шаблон ключа Камердинера](https://msdn.microsoft.com/library/dn568102.aspx).

Ниже приведен пример не указано время запуска политики общего доступа.

```
// The shared access policy provides  
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
   SharedAccessExpiryTime = DateTime.UtcNow.AddHours(10),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

Ниже приведен пример указано время запуска политики общего доступа со сроком действия больше пяти минут.

```
// The shared access policy provides  
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
  SharedAccessStartTime = new DateTime(2014,1,20),   
 SharedAccessExpiryTime = new DateTime(2014, 1, 21),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

Дополнительные сведения см. в разделе [Создание и использование подписи общего доступа](https://msdn.microsoft.com/library/azure/jj721951.aspx).

## <a name="use-cloudconfigurationmanager"></a>Используйте CloudConfigurationManager
### <a name="id"></a>ID
AP4000

### <a name="description"></a>Описание
С помощью [ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) класса для проектов, таких как веб-сайта Azure и мобильные службы Azure, не вызовет проблем времени выполнения. Рекомендуется, однако его рекомендуется использовать Cloud[ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) как единый способ управления конфигурациями всех облачных приложений Azure.

Поделитесь своими идеями и предложениями на [отзывов об анализе кода Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Причина
CloudConfigurationManager выполняет считывание файла конфигурации, подходит для среды приложения.

[CloudConfigurationManager](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx)

### <a name="solution"></a>Решение
Переработайте свой код для использования [класса CloudConfigurationManager](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx). Исправление кода для этой проблемы предоставляется с помощью средства анализа кода Azure.

В следующем фрагменте кода демонстрируется код исправления этой проблемы. Заменить

`var settings = ConfigurationManager.AppSettings["mySettings"];`

на

`var settings = CloudConfigurationManager.GetSetting("mySettings");`

Вот пример того, как сохранить параметры конфигурации в файле App.config или Web.config. Добавьте параметры в раздел appSettings файла конфигурации. Ниже приведен файл Web.config для предыдущего примера кода.

```
<appSettings>
    <add key="webpages:Version" value="3.0.0.0" />
    <add key="webpages:Enabled" value="false" />
    <add key="ClientValidationEnabled" value="true" />
    <add key="UnobtrusiveJavaScriptEnabled" value="true" />
    <add key="mySettings" value="[put_your_setting_here]"/>
  </appSettings>  
```

## <a name="avoid-using-hard-coded-connection-strings"></a>Избегайте использования жестко запрограммированных строк подключения
### <a name="id"></a>ID
AP4001

### <a name="description"></a>Описание
Если вы используете жестко запрограммированные строки подключения, и вам нужно обновить их позже, необходимо внести изменения в исходный код и перекомпилировать приложение. Тем не менее если вы храните строки подключения в файле конфигурации, можно изменить их позже, просто обновив файл конфигурации.

Поделитесь своими идеями и предложениями на [отзывов об анализе кода Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Причина
Жесткое программирование строки подключения не рекомендуется делать, так как она порождает проблемы, когда нужно быстро изменить строки подключения. Кроме того Если проект должен быть помещен систему управления версиями, жестко запрограммированные строки подключения появления уязвимостей, так как строки можно увидеть в исходном коде.

### <a name="solution"></a>Решение
Store строки подключения в файлах конфигурации или средах Azure.

* Для автономных приложений используйте файл app.config для хранения параметров строки подключения.
* Для размещенных в IIS веб-приложений используйте файл web.config для хранения строки подключения.
* Для приложений ASP.NET vNext используйте файл configuration.json для хранения строки подключения.

Сведения об использовании файлов конфигурации, например web.config или app.config, см. в разделе [правила веб-конфигурации ASP.NET](https://msdn.microsoft.com/library/vstudio/ff400235\(v=vs.100\).aspx). Сведения о том, как Azure работы переменных среды, см. в разделе [веб-сайтов Azure: How Application Strings and работы строками подключения](https://azure.microsoft.com/blog/2013/07/17/windows-azure-web-sites-how-application-strings-and-connection-strings-work/). Сведения о хранении строки подключения в системе управления версиями, см. в разделе [не указывать конфиденциальную информацию, например строки подключения в файлах, которые хранятся в репозитории исходного кода](http://www.asp.net/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/source-control).

## <a name="use-diagnostics-configuration-file"></a>Использование файла конфигурации диагностики
### <a name="id"></a>ID
AP5000

### <a name="description"></a>Описание
Вместо настройки параметров диагностики в коде, например, с помощью API программирования Microsoft.WindowsAzure.Diagnostics, следует настроить параметры диагностики в файле diagnostics.wadcfg. (Или diagnostics.wadcfgx, если вы используете Azure SDK 2.5). Таким образом, можно изменить параметры диагностики без повторной компиляции кода.

Поделитесь своими идеями и предложениями на [отзывов об анализе кода Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Причина
Прежде чем Azure SDK 2.5 (с использованием диагностики Azure 1.3), Azure Diagnostics (WAD) можно было настраивать с помощью нескольких различных методов: путем ее добавления в большой двоичный объект конфигурации в хранилище, с использованием императивного кода, декларативной конфигурации или значение по умолчанию Конфигурация. Тем не менее предпочтительным способом настройки диагностики является использование XML-файл конфигурации (diagnostics.wadcfg или diagnositcs.wadcfgx для пакета SDK 2.5 и более поздних версий) в проекте приложения. При таком подходе файл diagnostics.wadcfg полностью определяет конфигурацию и может обновляться и повторно развертываться по желанию. Совместное использование файла конфигурации diagnostics.wadcfg с программными методами настройки конфигураций при применении [DiagnosticMonitor](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.diagnosticmonitor.aspx)или [RoleInstanceDiagnosticManager](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.management.roleinstancediagnosticmanager.aspx)классы могут привести к путанице. См. в разделе [инициализация или изменение конфигурации службы диагностики Azure](https://msdn.microsoft.com/library/azure/hh411537.aspx) Дополнительные сведения.

Начиная с версии 1.3 службы WAD (входит в состав пакета Azure SDK 2.5), его больше нельзя использовать код для настройки диагностики. Таким образом вы может предоставить конфигурацию только при применении или обновлении расширения системы диагностики.

### <a name="solution"></a>Решение
Используйте конструктор конфигурации диагностики для перемещения параметров диагностики в файл конфигурации диагностики (diagnositcs.wadcfg или diagnositcs.wadcfgx для пакета SDK 2.5 и более поздних версий). Кроме того, рекомендуется установить [Azure SDK 2.5](http://go.microsoft.com/fwlink/?LinkId=513188) и использовать последние функции диагностики.

1. В контекстном меню для роли, которой вы хотите настроить выберите свойства и затем перейдите на вкладку конфигурации.
2. В **диагностики** разделе, убедитесь, что **включить диагностику** установлен флажок.
3. Выберите **Настройка** кнопки.

   ![Доступ к параметру "Включить диагностику"](./media/vs-azure-tools-optimizing-azure-code-in-visual-studio/IC796660.png)

   См. в разделе [Настройка системы диагностики для облачных служб Azure и виртуальных машин](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md) Дополнительные сведения.

## <a name="avoid-declaring-dbcontext-objects-as-static"></a>Не объявляйте объекты DbContext статическими
### <a name="id"></a>ID
AP6000

### <a name="description"></a>Описание
Для экономии памяти не объявляйте объекты DBContext статическими.

Поделитесь своими идеями и предложениями на [отзывов об анализе кода Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Причина
Объекты DBContext содержат результаты запроса из каждого вызова. Статические объекты DBContext не удаляются, пока не будет выгружен домен приложения. Таким образом статический объект DBContext может использовать большой объем памяти.

### <a name="solution"></a>Решение
Объявите DBContext как локальную переменную или поле нестатического экземпляра, используйте его для задачи и подождите, пока он будет удален после использования.

Приведенный пример класса контроллера MVC показывает, как использовать объект DBContext.

```
public class BlogsController : Controller
    {
        //BloggingContext is a subclass to DbContext        
        private BloggingContext db = new BloggingContext();
        // GET: Blogs
        public ActionResult Index()
        {
            //business logics…
            return View();
        }
        protected override void Dispose(bool disposing)
        {
            if (disposing)
            {
                db.Dispose();
            }
            base.Dispose(disposing);
        }
    }
```

## <a name="next-steps"></a>Следующие шаги
Для получения дополнительных сведений об оптимизации и устранении неполадок приложений Azure, см. в разделе [Устранение неполадок веб-приложения в службе приложений Azure с помощью Visual Studio](/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio).
