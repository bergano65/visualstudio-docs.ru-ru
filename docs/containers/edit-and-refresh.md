---
title: Отладка приложений в локальном контейнере Docker | Документация Майкрософт
description: Узнайте, как вносить изменения в приложение, выполняемое в локальном контейнере Docker, обновлять контейнер с помощью функций правки и обновления, а также устанавливать точки останова.
ms.author: ghogen
author: ghogen
manager: jillfra
ms.assetid: 480e3062-aae7-48ef-9701-e4f9ea041382
ms.topic: conceptual
ms.workload: multiple
ms.date: 07/25/2019
ms.technology: vs-azure
ms.openlocfilehash: 5af092bbcb987f45b10121f37d40eaa5466c3da5
ms.sourcegitcommit: 2db01751deeee7b2bdb1db25419ea6706e6fcdf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2019
ms.locfileid: "71126157"
---
# <a name="debug-apps-in-a-local-docker-container"></a>Отладка приложений в локальном контейнере Docker

Visual Studio обеспечивает согласованную разработку и проверку приложения в локальном контейнере Docker. Не нужно перезапустить контейнер каждый раз при внесении изменений в код.

В этой статье рассказывается, как запускать веб-приложение ASP.NET Core в локальном контейнере Docker с помощью Visual Studio, вносить изменения и обновлять браузер для их отображения. В ней также показано, как устанавливать точки останова для отладки контейнерных веб-приложений ASP.NET Core и консольных приложений .NET Framework.

## <a name="prerequisites"></a>Предварительные требования

Для отладки приложений в локальном контейнере Docker необходимо установить следующие средства:

::: moniker range="vs-2017"

* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) с установленной рабочей нагрузкой "Веб-разработка";

::: moniker-end

::: moniker range="vs-2019"

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) с установленной рабочей нагрузкой "Веб-разработка".

::: moniker-end

Для запуска контейнеров Docker локально требуется локальный клиент Docker. Можно воспользоваться версией [Docker Toolbox](https://www.docker.com/products/docker-toolbox), для которой требуется отключить Hyper-V. Можно также воспользоваться приложением [Docker для Windows](https://www.docker.com/get-docker), для которой требуются Hyper-V и Windows 10. 

Контейнеры Docker доступны для проектов .NET Framework и .NET Core. Рассмотрим два примера. Сначала мы рассмотрим веб-приложение .NET Core. Затем мы рассмотрим консольное приложение .NET Framework.

## <a name="create-a-web-app"></a>Создание веб-приложения

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">= vs-2019"
[!INCLUDE [create-aspnet5-app-2019](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

### <a name="edit-your-code-and-refresh"></a>Изменение и обновление кода

Для быстрой итерации изменений можно запустить приложение в контейнере. Затем продолжайте вносить изменения, просматривая их так же, как в IIS Express.

1. В качестве **конфигурации решения** выберите **Отладка**. Затем нажмите клавиши **CTRL**+**F5**, чтобы создать образ Docker и запустить его локально.

    После сборки и запуска образа контейнера в контейнере Docker среда Visual Studio запустит веб-приложение в вашем браузере по умолчанию.

2. Перейдите на страницу *Index* (Индекс). Мы будем вносить на ней изменения.
3. Вернитесь в Visual Studio и откройте файл *Index.cshtml*.
4. Добавьте приведенное ниже содержимое HTML в конец файла и сохраните изменения.

    ```html
    <h1>Hello from a Docker container!</h1>
    ```

5. Когда сборка .NET завершится и в окне вывода будут отображаться следующие строки, вернитесь в браузер и обновите страницу:

   ```output
   Now listening on: http://*:80
   Application started. Press Ctrl+C to shut down.
   ```

Изменения применены!

### <a name="debug-with-breakpoints"></a>Отладка с точками останова

Изменения часто требуют дальнейшей проверки. Для этого можно использовать функции отладки Visual Studio.

1. В Visual Studio откройте файл *Index.cshtml.cs*.
2. Замените содержимое метода `OnGet` следующим кодом:

   ```csharp
       ViewData["Message"] = "Your application description page from within a container";
   ```

3. Установите точку останова слева от строки кода.
4. Чтобы начать отладку и достичь точки останова, нажмите клавишу F5.
5. Переключитесь в Visual Studio, чтобы просмотреть точку останова. Проверьте значения.

   ![Точка останова](media/edit-and-refresh/breakpoint.png)

## <a name="create-a-net-framework-console-app"></a>Создание консольного приложения .NET Framework

При использовании проектов консольных приложений .NET Framework возможность добавления поддержки Docker без оркестрации недоступна. Описанную ниже процедуру можно выполнить, даже если вы используете только один проект Docker.

1. Создайте проект консольного приложения .NET Framework.
1. В обозревателе решений щелкните правой кнопкой мыши узел проекта и выберите **Добавить** > **Container Orchestration Support** (Поддержка оркестрации контейнеров).  В появившемся диалоговом окне выберите **Docker Compose**. Файл Dockerfile будет добавлен в проект, а проект Docker Compose со вспомогательными файлами будет добавлен в решение.

### <a name="debug-with-breakpoints"></a>Отладка с точками останова

1. В обозревателе решений откройте файл *Program.cs*.
2. Замените содержимое метода `Main` следующим кодом:

   ```csharp
       System.Console.WriteLine("Hello, world!");
   ```

3. Установите точку останова слева от строки кода.
4. Чтобы начать отладку и достичь точки останова, нажмите клавишу F5.
5. Переключитесь в Visual Studio, чтобы просмотреть точку останова и проверить значения.

   ![Точка останова](media/edit-and-refresh/breakpoint-console.png)

## <a name="container-reuse"></a>Повторное использование контейнеров

Во время цикла разработки среда Visual Studio перестраивает образы контейнеров и сам контейнер только при изменении файла Dockerfile. Если файл Dockerfile не изменяется, Visual Studio повторно использует контейнер из предыдущего запуска.

Если вы вручную изменили контейнер и хотите выполнить перезапуск с чистым образом контейнера, выберите команду **Сборка** > **Очистить**, а затем выполните сборку как обычную.

## <a name="troubleshoot"></a>Устранение неполадок

Узнайте, как [устранять неполадки при разработке Docker в Visual Studio](troubleshooting-docker-errors.md).

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>Дополнительные сведения об использовании Docker с Visual Studio, Windows и Azure

* Дополнительные сведения о [разработке контейнеров с помощью Visual Studio](/visualstudio/containers).
* Сведения о сборке и развертывании контейнера Docker см. в статье [Интеграция Docker для Azure Pipelines](https://aka.ms/dockertoolsforvsts).
* Указатель статей, посвященных Windows Server и Nano Server, см. на странице [Контейнеры в документации Windows](https://aka.ms/containers).
* Ознакомьтесь с общими сведениями о [Службе Azure Kubernetes](https://azure.microsoft.com/services/kubernetes-service/) и [документацией по Службе Azure Kubernetes](/azure/aks).
