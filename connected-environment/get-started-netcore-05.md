---
title: Создание среды разработки .NET Core с контейнерами с помощью Kubernetes в облаке — шаг 5 — вызов другого контейнера | Документы Майкрософт
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Быстрая разработка Kubernetes с контейнерами и микрослужбами в Azure
keywords: Docker, Kubernetes, Azure, AKS, служба контейнеров Azure, контейнеры
manager: ghogen
ms.openlocfilehash: 15ca1db26bc57aafa704a57b4464b31a1ada8c92
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core"></a>Начало работы в подключенной среде с .NET Core

Предыдущий шаг: [отладка контейнера в Kubernetes](get-started-netcore-04.md)

В этом разделе мы создадим вторую службу, `mywebapi`, к которой будет обращаться `webfrontend`. Каждая служба будет выполняться в отдельных контейнерах. Затем мы выполним отладку в обоих контейнерах.

![](media/multi-container.png)

## <a name="download-sample-code-for-mywebapi"></a>Загрузите пример кода для *mywebapi*
Чтобы сэкономить время, давайте загрузим пример кода из репозитория GitHub. Перейдите к https://github.com/Azure/vsce и выберите **Клонировать или загрузить**, чтобы загрузить репозиторий GitHub. Код для этого раздела находится в `vsce/samples/dotnetcore/getting-started/mywebapi`.


## <a name="run-mywebapi"></a>Запуск *mywebapi*
1. Откройте папку `mywebapi` в *отдельном окне VS Code*.
1. Нажмите клавишу F5 и подождите, пока выполнится сборка и развертывание службы. Когда все будет готово, откроется панель отладки VS Code.
1. Запишите URL-адрес конечной точки. Он будет иметь приблизительно такой вид: http://localhost:\<номер_порта\>. **Подсказка. В строке состояния VS Code отобразится URL-адрес, доступный для щелчка.** Может показаться, что контейнер выполняется локально, но фактически он выполняется в нашей среде разработки в Azure. В адресе указано localhost, потому что для `mywebapi` не определены общедоступные конечные точки и доступ осуществляется только в пределах экземпляра Kubernetes. Для вашего удобства и упрощения взаимодействия с закрытой службой на локальном компьютере подключенная среда создает временный туннель SSH для контейнера, запущенного в Azure.
1. Когда `mywebapi` будет готово, откройте в браузере адрес localhost. Добавьте `/api/values` к URL-адресу для вызова API GET по умолчанию для `ValuesController`. 
1. Если все шаги выполнены успешно, вы увидите ответ от службы `mywebapi`.


## <a name="make-a-request-from-webfrontend-to-mywebapi"></a>Запрос из *webfrontend* к *mywebapi*
Давайте теперь напишем код в `webfrontend`, который отправляет запрос в `mywebapi`.
1. Переключитесь на окно VS Code для `webfrontend`.
1. *Замените* код для метода About:

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

В приведенном выше примере кода также используется класс `HeaderPropagatingHttpClient`. Этот вспомогательный класс был добавлен в папку кода во время выполнения `vsce init`. `HeaderPropagatingHttpClient` является производным от хорошо известного класса `HttpClient`. Он позволяет распространять специальные заголовки из существующего объекта ASP .NET HttpRequest в исходящий объект HttpRequestMessage. Позже мы рассмотрим, как это помогает повысить производительность при коллективной разработке.


## <a name="debug-across-multiple-services"></a>Отладка в нескольких службах
1. На этом этапе служба `mywebapi` по-прежнему должна выполняться с подключенным отладчиком. Если это не так, нажмите клавишу F5 в проекте `mywebapi`.
1. Установите точку останова в методе `Get(int id)`, который обрабатывает запросы GET `api/values/{id}`.
1. В проекте `webfrontend` установите точку останова до отправки запроса GET в `mywebapi/api/values`.
1. Нажмите клавишу F5 в проекте `webfrontend`.
1. Вызовите веб-приложение и выполните пошаговое прохождение кода в обеих службах.
1. В веб-приложении на странице About отобразится объединенное сообщение от двух служб: "Привет от webfrontend и Привет от mywebapi".


Отлично! Теперь у вас есть приложение из нескольких контейнеров, где каждый контейнер можно разрабатывать и развертывать отдельно.

> [!div class="nextstepaction"]
> [Сведения о коллективной разработке](get-started-netcore-06.md)

