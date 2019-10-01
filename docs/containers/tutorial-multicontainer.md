---
title: Руководство по использованию нескольких контейнеров Docker Compose и ASP.NET Core
author: ghogen
description: Узнайте, как использовать несколько контейнеров с помощью Docker Compose
ms.author: ghogen
ms.date: 02/21/2019
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: ce6e98e2d068cd569247c4c4ea869c4280101d47
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2019
ms.locfileid: "71126091"
---
# <a name="tutorial-create-a-multi-container-app-with-docker-compose"></a>Учебник. Создание многоконтейнерного приложения с помощью Docker Compose

В этом руководстве описано, как управлять несколькими контейнерами и организовать между ними обмен данными с помощью инструментов Visual Studio для работы с контейнерами.  Для управления несколькими контейнерами требуется *оркестрация контейнеров* и оркестратор, например Docker Compose, Kubernetes или Service Fabric. Мы будем использовать Docker Compose. Docker Compose отлично подходит для локальной отладки и тестирования в течение цикла разработки.

## <a name="prerequisites"></a>Предварительные требования

::: moniker range="vs-2017"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) с установленной рабочей нагрузкой **Веб-разработка**, **Инструменты Azure** или **Кроссплатформенная разработка .NET Core**.
::: moniker-end

::: moniker range=">= vs-2019"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) с рабочей нагрузкой **Веб-разработка**, **Средства Azure** и (или) **Кроссплатформенная разработка .NET Core**.
* [Средства разработки .NET Core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2) для разработки с использованием .NET Core 2.2.
::: moniker-end

## <a name="create-a-web-application-project"></a>Создание проекта веб-приложения

В Visual Studio создайте проект **веб-приложения ASP.NET Core** с именем `WebFrontEnd`. Выберите **Веб-приложение**, чтобы создать веб-приложение с Razor Pages. 
  
::: moniker range="vs-2017"

Не выбирайте **Включение поддержки Docker**. Поддержка Docker будет добавлена позже.

![Снимок экрана: создание проекта веб-приложения](./media/tutorial-multicontainer/docker-tutorial-enable-docker-support.png)

::: moniker-end

::: moniker range="vs-2019"

![Снимок экрана: создание проекта веб-приложения](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project1.png)

Не выбирайте **Включение поддержки Docker**. Поддержка Docker будет добавлена позже.

![Снимок экрана: создание проекта веб-приложения](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project.png)

::: moniker-end

## <a name="create-a-web-api-project"></a>Создание проекта веб-API

Добавьте еще один проект в то же решение и назовите его *MyWebAPI*. Выберите тип проекта **API** и снимите флажок **Настроить для HTTPS**. В данном случае протокол SSL используется только для обмена данными с клиентом, но не для обмена данными между контейнерами в пределах веб-приложения. Протокол HTTPS требуется только для `WebFrontEnd`.

::: moniker range="vs-2017"
   ![Снимок экрана: создание проекта веб-API](./media/tutorial-multicontainer/docker-tutorial-mywebapi.png)
::: moniker-end
::: moniker range="vs-2019"
   ![Снимок экрана: создание проекта веб-API](./media/tutorial-multicontainer/vs-2019/web-api-project.png)
::: moniker-end

## <a name="add-code-to-call-the-web-api"></a>Добавление кода для вызова веб-API

1. В проекте `WebFrontEnd` откройте файл *Index.cshtml.cs* и замените текст метода `OnGet` следующим кодом.

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          request.RequestUri = new Uri("http://mywebapi/api/values/1");
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```

1. В файл *Index.cshtml* добавьте строку для отображения `ViewData["Message"]`, чтобы файл выглядел примерно так:
    
      ```cshtml
      @page
      @model IndexModel
      @{
          ViewData["Title"] = "Home page";
      }
    
      <div class="text-center">
          <h1 class="display-4">Welcome</h1>
          <p>Learn about <a href="https://docs.microsoft.com/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
          <p>@ViewData["Message"]</p>
      </div>
      ```

1. Теперь перейдите в проект веб-API и добавьте в контроллер Values код с пользовательским сообщением API для вызова, который вы добавили из *webfrontend*.
    
      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

1. В проекте `WebFrontEnd` выберите **Добавить > Container Orchestrator Support** (Поддержка оркестратора контейнеров). Появится диалоговое окно **Варианты поддержки Docker**.

1. Выберите **Docker Compose**.

1. Выберите целевую ОС, например Linux.

   ![Снимок экрана: выбор целевой ОС](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Visual Studio создаст файлы *docker-compose.yml* и *DOCKERIGNORE* в узле **docker-compose** решения. Этот проект выделен полужирным шрифтом, что значит, что это запускаемый проект.

   ![Снимок экрана обозревателя решений с добавленным проектом docker-compose](media/tutorial-multicontainer/multicontainer-solution-explorer.png)

   Файл *docker-compose.yml* выглядит так:

   ```yaml
   version: '3.4'

    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
   ```

   Файл *DOCKERIGNORE* содержит типы и расширения имен файлов, которые средству Docker не нужно включать в контейнер. Обычно эти файлы связаны со средой разработки и системой управления версиями, а не с самим разрабатываемым приложением или службой.

   Сведения о выполняемых командах приводятся в разделе **Инструменты для контейнера** области выходных данных.  Как вы можете видеть, программа командной строки docker-compose используется для настройки и создания контейнеров среды выполнения.

1. В проекте веб-API еще раз щелкните узел проекта правой кнопкой мыши и выберите пункт **Добавить** > **Container Orchestrator Support** (Поддержка оркестратора контейнеров). Выберите **Docker Compose**, а затем выберите ту же целевую ОС.  

    > [!NOTE]
    > На этом этапе Visual Studio предложит создать Dockerfile. Если сделать это для проекта, который уже поддерживает Docker, появится запрос на перезапись существующего файла Dockerfile. Если вы внесли изменения в Dockerfile, которые хотите сохранить, выберите "Нет".

    Visual Studio вносит ряд изменений в YML-файл docker-compose. Теперь включены обе службы.

    ```yaml
    version: '3.4'
    
    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
    
      mywebapi:
        image: ${DOCKER_REGISTRY-}mywebapi
        build:
          context: .
          dockerfile: MyWebAPI/Dockerfile
    ```

1. Теперь запустите сайт локально (F5 или CTRL+F5), чтобы убедиться в том, что он работает правильно. Если все настроено правильно, вы увидите следующее сообщение: "Hello from webfrontend and webapi (with value 1)" (Привет от webfrontend и веб-API (со значением 1)).

   Первый проект, используемый при добавлении оркестрации контейнеров, настраивается как начальный при запуске или отладке. Настроить действие запуска для проекта docker-compose можно в **свойствах проекта**.  Щелкните правой кнопкой мыши узел проекта docker-compose и выберите в контекстном меню пункт **Свойства** или нажмите клавиши ALT+ВВОД.  На снимке экрана ниже показаны свойства, которые требуются для решения в этом руководстве.  Например, можно изменить загружаемую страницу, настроив свойство **URL-адрес службы**.

   ![Снимок экрана: свойства проекта docker-compose](media/tutorial-multicontainer/launch-action.png)

   Вот что вы увидите при запуске:

   ![Снимок экрана с запущенным веб-приложением](media/tutorial-multicontainer/webfrontend.png)

## <a name="next-steps"></a>Следующие шаги

Ознакомьтесь с вариантами развертывания [контейнеров в Azure](/azure/containers).

## <a name="see-also"></a>См. также
  
[Docker Compose](https://docs.docker.com/compose/)  
[Инструменты для работы с контейнерами](/visualstudio/containers/)
