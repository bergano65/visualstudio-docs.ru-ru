---
title: Начало работы с Docker в Visual Studio для Mac
description: Сведения о добавлении Docker в проекты с помощью Visual Studio для Mac
author: asb3993
ms.author: amburns
ms.date: 06/17/2019
ms.openlocfilehash: b539de8159c1f53543b195f90610017bf2cee873
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2019
ms.locfileid: "67691701"
---
# <a name="get-started-with-docker-in-visual-studio-for-mac"></a>Начало работы с Docker в Visual Studio для Mac

В Visual Studio для Mac можно легко компилировать, отлаживать и выполнять контейнерные приложения ASP.NET Core, а также публиковать их в Azure.

## <a name="prerequisites"></a>Предварительные требования

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Visual Studio для Mac 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="installation-and-setup"></a>Установка и настройка

Чтобы установить Docker, изучите и выполните рекомендации из статьи [об установке Docker Desktop для Mac](https://docs.docker.com/docker-for-mac/install/).

## <a name="creating-an-aspnet-core-web-application-and-adding-docker-support"></a>Создание веб-приложения ASP.NET Core и добавление поддержки Docker

1. Создайте новое решение, выбрав **Файл > Создать решение**.
1. В разделе **.NET Core > Приложение** выберите шаблон **Веб-приложение**: ![Создание приложения ASP.NET](media/docker-quickstart-1.png)
1. Выберите целевую платформу. В нашем примере используется .NET Core 2.2: ![Указание целевой платформы](media/docker-quickstart-2.png)
1. Введите сведения о проекте, например имя (_DockerDemo_ в нашем примере). Созданный проект содержит все основные сведения, которые потребуются для сборки и запуска веб-сайта ASP.NET Core.
1. На панели решения щелкните проект DockerDemo правой кнопкой мыши и выберите **Добавить > Поддержка Docker**. ![Добавление поддержки Docker](media/docker-quickstart-3.png)

Visual Studio для Mac автоматически добавит в решение новый проект с именем **docker-compose**, а затем добавит в существующий проект файл **Dockerfile**.

![Автоматически созданные файлы поддержки Docker](media/docker-quickstart-4.png)

## <a name="dockerfile-overview"></a>Общие сведения о Dockerfile

Dockerfile содержит инструкции по созданию окончательного образа Docker. См. [справочник по Dockerfile](https://docs.docker.com/engine/reference/builder/) для получения сведений о других доступных в нем командах.

```
FROM microsoft/dotnet:2.2-aspnetcore-runtime AS base
WORKDIR /app
EXPOSE 80

FROM microsoft/dotnet:2.2-sdk AS build
WORKDIR /src
COPY DockerDemo/DockerDemo.csproj DockerDemo/
RUN dotnet restore DockerDemo/DockerDemo.csproj
COPY . .
WORKDIR /src/DockerDemo
RUN dotnet build DockerDemo.csproj -c Release -o /app

FROM build AS publish
RUN dotnet publish DockerDemo.csproj -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "DockerDemo.dll"]
```

Предыдущий *Dockerfile* основан на образе [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) и включает в себя инструкции по изменению базового образа путем сборки проекта и добавления его в контейнер.

> [!NOTE]
> По умолчанию файл Dockerfile, созданный в Visual Studio для Mac, открывает порт 80 для HTTP-трафика. Чтобы включить HTTPS-трафик, добавьте `Expose 443` в Dockerfile.

## <a name="debugging"></a>Отладка

Настройте проект `docker-compose` в качестве запускаемого проекта и запустите отладку (**Пуск > Начать отладку**). Эта команда компилирует, развертывает и запускает проект ASP.NET в контейнере.

> [!TIP]
> Во время первого запуска после установки Docker Desktop может появиться следующая ошибка при попытке отладки: `Cannot start service dockerdemo: Mounts denied`
> 
> Добавьте `/usr/local/share/dotnet/sdk/NuGetFallbackFolder` на вкладку общего доступа в Docker Desktop:
>
> ![Добавление папки NuGetFallbackFolder в раздел общего доступа](media/docker-quickstart-5.png)

Когда сборка завершится, приложение откроется в браузере Safari:

![Проект Docker по умолчанию, запущенный в Safari](media/docker-quickstart-6.png)

Обратите внимание, что контейнер будет прослушивать некоторый порт (например, `http://localhost:32768`) номер которого может быть разным.

Чтобы просмотреть список выполняемых контейнеров, выполните команду `docker ps` в терминале.

Обратите внимание на ретранслятор портов на следующем снимке экрана (в разделе **PORTS** (Порты)). Это означает, что контейнер прослушивает порт, который мы ранее открывали в браузере Safari, и передает все запросы на внутренний веб-сервер через порт 80 (как определено в файле Dockerfile). Само приложение считает, что прослушивает порт 80:

![Список контейнеров Docker](media/docker-quickstart-7.png)
