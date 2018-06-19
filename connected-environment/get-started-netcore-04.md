---
title: Создание среды разработки .NET Core с контейнерами с помощью Kubernetes в облаке — шаг 4 — отладка контейнера в Kubernetes | Документы Майкрософт
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Быстрая разработка Kubernetes с контейнерами и микрослужбами в Azure
keywords: Docker, Kubernetes, Azure, AKS, служба контейнеров Azure, контейнеры
manager: douge
ms.openlocfilehash: 043052dec78251647a3ef12e0b612355b6334692
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31886297"
---
# <a name="get-started-on-connected-environment-with-net-core"></a>Начало работы в подключенной среде с .NET Core
 
Предыдущий шаг: [создание веб-приложения ASP.NET Core](get-started-netcore-03.md)

[!INCLUDE[](includes/debug-intro.md)]

[!INCLUDE[](includes/init-debug-assets-vscode.md)]


## <a name="select-the-vsce-debug-configuration"></a>Выбор конфигурации отладки VSCE
1. Чтобы открыть представление отладки, щелкните значок отладки в **строке активности** в боковой части VS Code.
1. Выберите **Запуск .NET Core (VSCE)** в качестве активной конфигурации отладки.

![](media/debug-configuration.png)

> [!Note]
> Если вы не видите команды подключенной среды в палитре команд, убедитесь, что [установили расширения VS Code для подключенной среды](get-started-netcore-01.md#get-kubernetes-debugging-for-vs-code).


## <a name="debug-the-container-in-kubernetes"></a>Отладка контейнера в Kubernetes
Нажмите **F5** для отладки кода в Kubernetes.

Как и при выполнении команды `up`, код синхронизируется со средой разработки, и выполняется сборка и развертывание контейнера в Kubernetes. На этот раз, разумеется, отладчик прикреплен к удаленному контейнеру.

[!INCLUDE[](includes/tip-vscode-status-bar-url.md)]

Установите точку останова в файле кода на стороне сервера, например в функции `Index()` в исходном файле `Controllers/HomeController.cs`. Обновление страницы браузера приводит к срабатыванию точки останова.

У вас будет полный доступ к сведениям об отладке, как если бы код выполнялся локально, например стек вызовов, локальные переменные, сведения об исключениях и т. д.

## <a name="edit-code-and-refresh"></a>Редактирование кода и обновление
Внесите правку, когда отладчик активен. Например, измените сообщение на странице About в `Controllers/HomeController.cs`. 

```csharp
public IActionResult About()
{
    ViewData["Message"] = "My custom message in the About page.";
    return View();
}
```

Сохраните файл и на **панели действий отладки** нажмите кнопку **Обновить**. 

![](media/debug-action-refresh.png)

Вместо повторной сборки и развертывания нового образа контейнера при каждой правке, что часто занимает немало времени, подключенная среда будет постепенно перекомпилировать код в существующем процессе, чтобы ускорить цикл правки и отладки.

Обновите веб-приложение в браузере и перейдите на страницу About. Вы увидите ваше сообщение в пользовательском интерфейсе.

**Теперь у вас есть метод для быстрой итерации кода и отладки непосредственно в Kubernetes.** Далее вы узнаете, как создать и вызвать второй контейнер.

> [!div class="nextstepaction"]
> [Вызов службы, запущенной в отдельном контейнере](get-started-netcore-05.md)
