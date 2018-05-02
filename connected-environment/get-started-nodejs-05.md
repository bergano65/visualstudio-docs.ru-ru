---
title: Создание среды разработки Node.js с контейнерами с помощью Kubernetes в облаке — шаг 5 — вызов другого контейнера | Документы Майкрософт
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Быстрая разработка Kubernetes с контейнерами и микрослужбами в Azure
keywords: Docker, Kubernetes, Azure, AKS, служба контейнеров Azure, контейнеры
manager: douge
ms.openlocfilehash: 89565869feec746aff75327b59ee7d0b466f26c1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Начало работы в подключенной среде с Node.js

Предыдущий шаг: [отладка контейнера в Kubernetes](get-started-nodejs-04.md)

В этом разделе мы создадим вторую службу, `mywebapi`, к которой будет обращаться `webfrontend`. Каждая служба будет выполняться в отдельных контейнерах. Затем мы выполним отладку в обоих контейнерах.

![](media/multi-container.png)

## <a name="open-sample-code-for-mywebapi"></a>Откройте пример кода для *mywebapi*
У вас уже должен быть пример кода для `mywebapi` в рамках этого руководства. Он находится в папке `vsce/samples` (в противном случае перейдите к https://github.com/Azure/vsce и выберите **Клонировать или загрузить**, чтобы загрузить репозиторий GitHub). Код для этого раздела находится в `vsce/samples/nodejs/getting-started/mywebapi`.

## <a name="run-mywebapi"></a>Запуск *mywebapi*
1. Откройте папку `mywebapi` в *отдельном окне VS Code*.
1. Нажмите клавишу F5 и подождите, пока выполнится сборка и развертывание службы. Когда все будет готово, откроется панель отладки VS Code.
1. Запишите URL-адрес конечной точки. Он будет иметь приблизительно такой вид: http://localhost:\<номер_порта\>. **Подсказка. В строке состояния VS Code отобразится URL-адрес, доступный для щелчка.** Может показаться, что контейнер выполняется локально, но фактически он выполняется в нашей среде разработки в Azure. В адресе указано localhost, потому что для `mywebapi` не определены общедоступные конечные точки и доступ осуществляется только в пределах экземпляра Kubernetes. Для вашего удобства и упрощения взаимодействия с закрытой службой на локальном компьютере подключенная среда создает временный туннель SSH для контейнера, запущенного в Azure.
1. Когда `mywebapi` будет готово, откройте в браузере адрес localhost. Вы увидите ответ от службы `mywebapi` ("Привет от mywebapi").


## <a name="make-a-request-from-webfrontend-to-mywebapi"></a>Запрос из *webfrontend* к *mywebapi*
Давайте теперь напишем код в `webfrontend`, который отправляет запрос в `mywebapi`.
1. Переключитесь на окно VS Code для `webfrontend`.
1. Добавьте следующие строки кода в верхней части `server.js`:
```javascript
var request = require('request');
var propagateHeaders = require('./propagateHeaders');
```

3. *Замените* код для обработчика GET `/api`. При обработке запроса он, в свою очередь, обращается к `mywebapi`, а затем возвращает результаты из обеих служб.

```javascript
app.get('/api', function (req, res) {
    request({
        uri: 'http://mywebapi',
        headers: propagateHeaders.from(req) // propagate headers to outgoing requests
    }, function (error, response, body) {
        res.send('Hello from webfrontend and ' + body);
    });
});
```

Обратите внимание на то, как используется обнаружение службы DNS Kubernetes для обращения к службе в качестве `http://mywebapi`. **Код в нашей среде разработки выполняется так же, как он будет выполняться в рабочей среде**.

В приведенном выше примере кода используется вспомогательный модуль с именем `propagateHeaders`. Этот вспомогательный модуль был добавлен в папку кода во время выполнения `vsce init`. Функция `propagateHeaders.from()` распространяет определенные заголовки из существующего объекта http.IncomingMessage для исходящего запроса. Позже мы рассмотрим, как это помогает повысить производительность при коллективной разработке.


## <a name="debug-across-multiple-services"></a>Отладка в нескольких службах
1. На этом этапе служба `mywebapi` по-прежнему должна выполняться с подключенным отладчиком. Если это не так, нажмите клавишу F5 в проекте `mywebapi`.
1. Установите точку останова в обработчике GET `/` по умолчанию.
1. В проекте `webfrontend` установите точку останова до отправки запроса GET в `http://mywebapi`.
1. Нажмите клавишу F5 в проекте `webfrontend`.
1. Откройте веб-приложение и выполните пошаговое прохождение кода в обеих службах. В веб-приложении должно отобразиться объединенное сообщение от двух служб: "Привет от webfrontend и Привет от mywebapi".


Отлично! Теперь у вас есть приложение из нескольких контейнеров, где каждый контейнер можно разрабатывать и развертывать отдельно.

> [!div class="nextstepaction"]
> [Сведения о коллективной разработке](get-started-nodejs-06.md)
