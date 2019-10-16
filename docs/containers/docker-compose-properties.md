---
title: Параметры сборки Docker Compose для инструментов Visual Studio для работы с контейнерами
author: ghogen
description: Обзор процесса сборки с помощью инструментов для работы с контейнерами
ms.author: ghogen
ms.date: 08/12/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 2178881c6ea0e597aef5e25074e3648162d3f6e9
ms.sourcegitcommit: 6ae0a289f1654dec63b412bfa22035511a2ef5ad
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950636"
---
# <a name="docker-compose-build-properties"></a>Свойства сборки Docker Compose

Помимо свойств для отдельных проектов Docker (см. статью [Свойства сборки с помощью инструментов для работы с контейнерами](container-msbuild-properties.md)), вы можете настроить способ сборки проектов Docker Compose в Visual Studio, задав свойства Docker Compose, используемые MSBuild для сборки решения. Кроме того, вы можете управлять запуском приложений Docker Compose с помощью отладчика Visual Studio. Для этого необходимо задать метки файлов в файлах конфигурации Docker Compose.

## <a name="how-to-set-the-msbuild-properties"></a>Задание свойств MSBuild

Чтобы задать значение свойства, измените файл проекта. Для свойств Docker Compose этот файл проекта имеет расширение DCPROJ, если иное не указано в таблице в следующем разделе. Например, предположим, что при начале отладки должен запускаться браузер. Вы можете задать свойство `DockerLaunchAction` в файле проекта DCPROJ указанным ниже образом.

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

Вы можете добавить значение свойства в существующий элемент `PropertyGroup` или, если его нет, создать новый элемент `PropertyGroup`.

## <a name="docker-compose-msbuild-properties"></a>Свойства MSBuild для Docker Compose

В таблице ниже приводятся свойства MSBuild, доступные для проектов Docker Compose.

| Имя свойства | Местоположение | ОПИСАНИЕ | Значение по умолчанию  |
|---------------|----------|-------------|----------------|
|DockerComposeBuildArguments|DCPROJ|Указывает дополнительные параметры, передаваемые в команду `docker-compose build`. Например: `--parallel --pull` |
|DockerComposeDownArguments|DCPROJ|Указывает дополнительные параметры, передаваемые в команду `docker-compose down`. Например: `--timeout 500`|-|  
|DockerComposeProjectPath|CSPROJ или VBPROJ|Относительный путь к файлу проекта docker-compose (DCPROJ). Задайте это свойство при публикации проекта службы, чтобы можно было найти связанные параметры сборки образа, хранящиеся в файле docker-compose.yml.|-|
|DockerComposeUpArguments|DCPROJ|Указывает дополнительные параметры, передаваемые в команду `docker-compose up`. Например: `--timeout 500`|-|
|DockerLaunchAction| DCPROJ | Указывает действие запуска, выполняемое при нажатии клавиши F5 или клавиш CTRL+F5.  Допустимые значения: None, LaunchBrowser и LaunchWCFTestClient|Нет|
|DockerLaunchBrowser| DCPROJ | Указывает, следует ли запускать браузер. Игнорируется, если задано свойство DockerLaunchAction. | False |
|DockerServiceName| DCPROJ|Если указано свойство DockerLaunchAction или DockerLaunchBrowser, DockerServiceName — это имя службы, которую следует запустить.  Используйте это свойство, чтобы указать, какой из множества проектов, на которые может ссылаться файл docker-compose, будет запущен.|-|
|DockerServiceUrl| DCPROJ | URL-адрес, используемый при запуске браузера.  Допустимые токены замены: "{ServiceIPAddress}", "{ServicePort}" и "{Scheme}".  Пример: {Scheme}://{ServiceIPAddress}:{ServicePort}|-|
|DockerTargetOS| DCPROJ | Целевая ОС, используемая при сборке образа Docker.|-|

> [!NOTE]
> Свойства DockerComposeBuildArguments, DockerComposeDownArguments и DockerComposeUpArguments появились в Visual Studio 2019 версии 16.3.

## <a name="docker-compose-file-labels"></a>Метки файлов Docker Compose

Некоторые параметры можно также переопределить, поместив файл *docker-compose.vs.debug.yml* (для конфигурации **отладки**) или *docker-compose.vs.release.yml* (для конфигурации **выпуска**) в один каталог с файлом *docker-compose.yml*.  В этом файле можно задать перечисленные ниже параметры.

```yml
services:
  webapplication1:
    labels:
      com.microsoft.visualstudio.debuggee.workingdirectory: "C:\\my_app_folder"
```

Заключайте значения в двойные кавычки, как в предыдущем примере, и используйте обратную косую черту как escape-символ для обратных косых черт в путях.

|Имени метки|ОПИСАНИЕ|
|----------|-----------|
|com.microsoft.visualstudio.debuggee.arguments|Аргументы, передаваемые в программу при запуске отладки. Для приложений .NET Core эти аргументы обычно представляют собой дополнительные пути поиска пакетов NuGet, за которыми следует путь к выходной сборке проекта.|
|com.microsoft.visualstudio.debuggee.killprogram|Эта команда служит для остановки отлаживаемой программы, выполняемой в контейнере (при необходимости).|
|com.microsoft.visualstudio.debuggee.program|Программа, запускаемая при начале отладки. Для приложений .NET Core этот параметр обычно имеет значение **dotnet**.|
|com.microsoft.visualstudio.debuggee.workingdirectory|Каталог, используемый в качестве начального при запуске отладки. Этот параметр обычно имеет значение */app* для контейнеров Linux или *C:\app* для контейнеров Windows.|

## <a name="next-steps"></a>Следующие шаги

Общие сведения о свойствах MSBuild см. в статье [Свойства MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>См. также

[Свойства сборки с помощью инструментов для работы с контейнерами](container-msbuild-properties.md)

[Параметры запуска инструментов для работы с контейнерами](container-launch-settings.md)

[Зарезервированные и стандартные свойства MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)