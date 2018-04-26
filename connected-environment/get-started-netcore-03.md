---
title: Создание среды разработки .NET Core с контейнерами с помощью Kubernetes в облаке — шаг 3 — создание веб-приложения ASP.NET Core | Документы Майкрософт
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Быстрая разработка Kubernetes с контейнерами и микрослужбами в Azure
keywords: Docker, Kubernetes, Azure, AKS, служба контейнеров Azure, контейнеры
manager: douge
ms.openlocfilehash: 72c7df0a82b91f7b4665b8b7e2cecdfc2eea26cf
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-net-core"></a>Начало работы в подключенной среде с .NET Core

Предыдущий шаг: [создание среды разработки Kubernetes в Azure](get-started-netcore-02.md)

## <a name="create-an-aspnet-core-web-app"></a>Создание веб-приложения ASP.NET Core
Если у вас установлен [.NET Core](https://www.microsoft.com/net), вы можете быстро создать веб-приложение ASP.NET Core в папке с именем `webfrontend`.
```cmd
dotnet new mvc --name webfrontend
```

В противном случае **загрузите пример кода из GitHub**, перейдя к https://github.com/Azure/vsce, и выберите **Клонировать или загрузить**, чтобы загрузить репозиторий GitHub в локальную среду. Код для этого руководства находится в `vsce/samples/dotnetcore/getting-started/webfrontend`.

[!INCLUDE[](includes/vsce-init.md)]

[!INCLUDE[](includes/ensure-env-created.md)]

[!INCLUDE[](includes/build-and-run-in-k8s-cli.md)]

## <a name="update-a-content-file"></a>Обновите файл содержимого
Подключенная среда связана не только с получением кода, выполняемого в Kubernetes. Это возможность быстро и последовательно отслеживать, как изменения кода вступают в силу в среде Kubernetes в облаке.

1. Найдите файл `./Views/Home/Index.cshtml` и внесите изменения в HTML. Например, измените строку 70 с содержанием `<h2>Application uses</h2>` на: `<h2>Hello k8s in Azure!</h2>`
1. Сохраните файл. Почти сразу в окне терминала вы увидите сообщение о том, что файл в выполняемом контейнере был изменен.
1. Перейдите в браузер и обновите страницу. На веб-странице будет отображаться обновленный HTML-код.

Что произошло? Изменения, вносимые в файлы содержимого, например HTML и CSS, не требуют повторной компиляции в веб-приложении .NET Core, поэтому активная команда `vsce up` автоматически синхронизирует все измененные файлы содержимого в выполняемом контейнере в Azure, тем самым обеспечивая возможность быстрого просмотра изменений.

## <a name="update-a-code-file"></a>Обновление файла кода
Обновление файлов кода требует дополнительных усилий, поскольку приложение .NET Core должно перестроиться и создать обновленный двоичный код приложения.

1. В окне терминала введите `Ctrl+C` (чтобы остановить `vsce up`).
1. Откройте файл кода с именем `Controllers/HomeController.cs` и измените сообщение, отображающееся на странице "О программе": `ViewData["Message"] = "Your application description page.";`
1. Сохраните файл.
1. Запустите `vsce up` в окне терминала. 

Образ контейнера будет перестроен, а диаграмма Helm будет повторно развернута. Чтобы увидеть изменения кода в работающем приложении, перейдите в меню "О программе" в веб-приложении.


Но существует еще более *быстрый метод* создания кода, который мы обсудим в следующем разделе. 
> [!div class="nextstepaction"]
> [Отладка контейнера в Kubernetes](get-started-netcore-04.md)

