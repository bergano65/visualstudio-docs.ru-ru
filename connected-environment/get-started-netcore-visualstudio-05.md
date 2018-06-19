---
title: Создание среды разработки .NET Core с контейнерами с помощью Kubernetes в облаке с Visual Studio — шаг 5 — вызов другого контейнера | Документы Майкрософт
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Быстрая разработка Kubernetes с контейнерами и микрослужбами в Azure
keywords: Docker, Kubernetes, Azure, AKS, служба контейнеров Azure, контейнеры
manager: douge
ms.openlocfilehash: ab3934e6f7f013dd21309dc8c98461983bdfe30a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31898431"
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Начало работы в подключенной среде с .NET Core и Visual Studio

Предыдущий шаг: [отладка контейнера в Kubernetes](get-started-netcore-visualstudio-04.md)

## <a name="call-another-container"></a>Вызов другого контейнера
В этом разделе мы создадим вторую службу, `mywebapi`, к которой будет обращаться `webfrontend`. Каждая служба будет выполняться в отдельных контейнерах. Затем мы выполним отладку в обоих контейнерах.

![](media/multi-container.png)

## <a name="download-sample-code-for-mywebapi"></a>Загрузите пример кода для *mywebapi*
Чтобы сэкономить время, давайте загрузим пример кода из репозитория GitHub. Перейдите к https://github.com/Azure/vsce и выберите **Клонировать или загрузить**, чтобы загрузить репозиторий GitHub. Код для этого раздела находится в `vsce/samples/dotnetcore/getting-started/mywebapi`.

## <a name="run-mywebapi"></a>Запуск *mywebapi*
1. Откройте проект `mywebapi` в *отдельном окне Visual Studio*.
1. Выберите **Подключенная среда для AKS** из раскрывающегося списка параметров запуска, как вы делали ранее для проекта `webfrontend`. Вместо создания новой среды разработки на этот раз выберите ту, что вы уже создали. Как и ранее, оставьте пространство по умолчанию `mainline` и нажмите **ОК**. В окне вывода вы увидите, что Visual Studio начинает "разогревать" новую службу в вашей среде разработки, чтобы ускорить процесс при запуске отладки.
1. Нажмите клавишу F5 и подождите, пока выполнится сборка и развертывание службы. Вы узнаете, что все готово, когда строка состояния Visual Studio станет оранжевой
1. Запишите URL-адрес конечной точки, который отображается на панели **Подключенная среда для AKS** в окне **Вывод**. Он будет иметь примерно следующий вид: http://localhost:\<номер_порта\>. Может показаться, что контейнер выполняется локально, но фактически он выполняется в нашей среде разработки в Azure.
1. Когда `mywebapi` будет готово, откройте в браузере адрес localhost и добавьте `/api/values` к URL-адресу для вызова API GET по умолчанию для `ValuesController`. 
1. Если все шаги выполнены успешно, вы увидите ответ от службы `mywebapi`. Он будет выглядеть следующим образом.

    ![](images/WebAPIResponse.png)

## <a name="make-a-request-from-webfrontend-to-mywebapi"></a>Запрос из *webfrontend* к *mywebapi*
Давайте теперь напишем код в `webfrontend`, который отправляет запрос в `mywebapi`. Переключитесь в окно Visual Studio с проектом `webfrontend`. В файле `HomeController.cs` *замените* код для метода About следующим:

 ```csharp
    public async Task<IActionResult> About()
    {
        ViewData["Message"] = "Hello from webfrontend";
        
        // Use HeaderPropagatingHttpClient instead of HttpClient so we can propagate
        // headers in the incoming request to any outgoing requests
        using (var client = new HeaderPropagatingHttpClient(this.Request))
        {
            // Call *mywebapi*, and display its response in the page
            var response = await client.GetAsync("http://mywebapi/api/values/1");
            ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
        }
    
        return View();
    }

```

Обратите внимание на то, как используется обнаружение службы DNS Kubernetes для обращения к службе в качестве `http://mywebapi`. **Код в нашей среде разработки выполняется так же, как он будет выполняться в рабочей среде**.

В приведенном выше примере кода также используется класс `HeaderPropagatingHttpClient`. Этот вспомогательный класс — файл `HeaderPropagation.cs`, добавленный в проект при настройке подключенной среды. `HeaderPropagatingHttpClient` является производным от хорошо известного класса `HttpClient`. Он позволяет распространять специальные заголовки из существующего объекта ASP .NET HttpRequest в исходящий объект HttpRequestMessage. Позже мы рассмотрим, как это помогает повысить производительность при коллективной разработке.

## <a name="debug-across-multiple-services"></a>Отладка в нескольких службах
1. На этом этапе служба `mywebapi` по-прежнему должна выполняться с подключенным отладчиком. Если это не так, нажмите клавишу F5 в проекте `mywebapi`.
1. Установите точку останова в методе `Get(int id)` в файле `ValuesController.cs`, который обрабатывает запросы GET `api/values/{id}`.
1. В проекте `webfrontend`, куда мы вставили указанный выше код, установите точку останова до отправки запроса GET в `mywebapi/api/values`.
1. Нажмите клавишу F5 в проекте `webfrontend`. Visual Studio снова откроет браузер по адресу localhost, где будет отображаться веб-приложение.
1. Нажмите на ссылку "**About**" в верхней части страницы для запуска точки останова в проекте `webfrontend`. 
1. Нажмите клавишу F10, чтобы продолжить. Точка останова в проекте `mywebapi` будет активирована.
1. Нажмите F5, чтобы продолжить, и вы вернетесь к коду проекта `webfrontend`.
1. Нажмите клавишу F5 еще раз для выполнения запроса и возврата страницы в браузере. В веб-приложении на странице About отобразится объединенное сообщение от двух служб: "Привет от webfrontend и Привет от mywebapi".

Отлично! Теперь у вас есть приложение из нескольких контейнеров, где каждый контейнер можно разрабатывать и развертывать отдельно.

> [!div class="nextstepaction"]
> [Сведения о коллективной разработке](get-started-netcore-visualstudio-06.md)

