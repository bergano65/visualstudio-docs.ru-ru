---
title: Руководство. Создание многоконтейнерного приложения с помощью Docker Compose
description: Узнайте, как управлять несколькими контейнерами и организовать между ними обмен данными в Visual Studio для Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 06/17/2019
ms.openlocfilehash: 487945399252ca3627d625e3572637b5b2af2916
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2019
ms.locfileid: "74983954"
---
# <a name="create-a-multi-container-app-with-docker-compose"></a>Создание многоконтейнерного приложения с помощью Docker Compose

В этом руководстве описано, как управлять несколькими контейнерами и организовать между ними обмен данными в Visual Studio для Mac.

## <a name="prerequisites"></a>Предварительные требования

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Visual Studio для Mac 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="create-an-aspnet-core-web-application-and-add-docker-support"></a>Создание веб-приложения ASP.NET Core и добавление поддержки Docker

1. Создайте новое решение, выбрав **Файл > Создать решение**.
1. В разделе **.NET Core > Приложение** выберите шаблон **Веб-приложение**: ![Создание приложения ASP.NET](media/docker-quickstart-1.png)
1. Выберите целевую платформу. В нашем примере используется .NET Core 2.2: ![Указание целевой платформы](media/docker-quickstart-2.png)
1. Введите сведения о проекте, например имя проекта (_DockerDemoFrontEnd_ в нашем примере) и имя решения (_DockerDemo_). Созданный проект содержит все основные сведения, которые потребуются для сборки и запуска веб-сайта ASP.NET Core.
1. На панели решений щелкните проект DockerDemoFrontEnd правой кнопкой мыши и выберите **Добавить > Поддержка Docker**. ![Добавление поддержки Docker](media/docker-quickstart-3.png)

Visual Studio для Mac автоматически добавит в решение новый проект с именем **docker-compose**, а затем добавит в существующий проект файл **Dockerfile**.

## <a name="create-an-aspnet-core-web-api-and-add-docker-support"></a>Создание веб-интерфейса ASP.NET Core и добавление поддержки Docker

Теперь мы создадим второй проект, который будет выполнять роль API серверной части. Шаблон **.NET Core API** содержит контроллер, который позволяет обрабатывать запросы RESTful.

1. Добавьте новый проект в существующее решение, щелкнув решение правой кнопкой мыши и выбрав **Добавить > Новый проект**.
1. В разделе **.NET Core > Приложение** выберите шаблон **API**.
1. Выберите целевую платформу. В нашем примере используется .NET Core 2.2.
1. Введите сведения о проекте, например имя проекта (_DockerDemoFrontEnd_ в нашем примере).
1. Завершив создание, откройте Панель решения и щелкните проект DockerDemoAPI правой кнопкой мыши, затем выберите **Добавить > Поддержка Docker**.

Файл **docker-compose.yml** в проекте **docker-compose** будет автоматически обновлен для размещения проекта API рядом с уже существующим проектом веб-приложения. После сборки и запуска проекта **docker-compose** оба этих проекта будут развернуты в отдельных контейнерах Docker.

```
version: '3.4'

services:
  dockerdemofrontend:
    image: ${DOCKER_REGISTRY-}dockerdemofrontend
    build:
      context: .
      dockerfile: DockerDemoFrontEnd/Dockerfile

  dockerdemoapi:
    image: ${DOCKER_REGISTRY-}dockerdemoapi
    build:
      context: .
      dockerfile: DockerDemoAPI/Dockerfile
```

## <a name="integrate-the-two-containers"></a>Интеграция двух контейнеров

Теперь в нашем решении есть два проекта ASP.NET, для каждого из которых настроена поддержка Docker. Теперь нам нужно добавить в них код.

1. В проекте `DockerDemoFrontEnd` откройте файл *Index.cshtml.cs* и замените текст метода `OnGet` следующим кодом:

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          request.RequestUri = new Uri("http://dockerdemoapi/api/values/1");
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

1. Теперь перейдите в проект веб-API и добавьте в контроллер Values код с пользовательским сообщением API для вызова, который вы добавили из *webfrontend*:

      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

1. Настройте проект `docker-compose` в качестве запускаемого проекта и запустите команду **Пуск > Начать отладку**. Если все настроено правильно, вы увидите следующее сообщение: Hello from webfrontend and webapi (with value 1) (Привет от webfrontend и веб-API (со значением 1)), как показано ниже:

![Выполнение решения с несколькими контейнерами docker](media/docker-multicontainer-debug.png)
