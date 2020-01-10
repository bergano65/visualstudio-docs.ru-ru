---
title: Расширенный пример для контейнеров
description: ''
ms.date: 07/03/2019
ms.topic: conceptual
ms.assetid: e03835db-a616-41e6-b339-92b41d0cfc70
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 539b21c474f9c119427e7f74192e80e7686b299c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588540"
---
# <a name="advanced-example-for-containers"></a>Расширенный пример для контейнеров

::: moniker range="vs-2017"

Пример файла Dockerfile, приведенный в разделе [Установка средств сборки в контейнер](build-tools-container.md), всегда использует образ [microsoft/dotnet-framework:4.7.2](https://hub.docker.com/r/microsoft/dotnet-framework) на основе последней версии образа microsoft/windowsservercore и последнюю версию установщика Visual Studio Build Tools. Если вы публикуете этот образ в [реестре Docker](https://azure.microsoft.com/services/container-registry), чтобы его могли извлекать другие пользователи, то во многих случаях он будет подходящим. Однако на практике чаще требуется использовать определенный базовый образ, скачивать определенные двоичные файлы и устанавливать определенные версии средств.

::: moniker-end

::: moniker range="vs-2019"

Пример файла Dockerfile, приведенный в разделе [Установка средств сборки в контейнер](build-tools-container.md), всегда использует образ [microsoft/dotnet-framework:4.8](https://hub.docker.com/r/microsoft/dotnet-framework) на основе последней версии образа microsoft/windowsservercore и последнюю версию установщика Visual Studio Build Tools. Если вы публикуете этот образ в [реестре Docker](https://azure.microsoft.com/services/container-registry), чтобы его могли извлекать другие пользователи, то во многих случаях он будет подходящим. Однако на практике чаще требуется использовать определенный базовый образ, скачивать определенные двоичные файлы и устанавливать определенные версии средств.

::: moniker-end

Приведенный ниже пример файла Dockerfile использует конкретный тег версии образа microsoft/dotnet-framework. Применение определенного тега для базового образа — распространенная практика. Таким образом вы не забудете, что для сборки или повторной сборки образов должна использоваться одна и та же основа.

> [!NOTE]
> Среду Visual Studio невозможно установить в образе microsoft/windowsservercore:10.0.14393.1593 или любом основанном на нем образе, так как в нем имеются известные проблемы с запуском установщика в контейнере. Дополнительные сведения см. в статье об [известных проблемам с контейнерами](build-tools-container-issues.md).

В приведенном ниже примере скачивается последний выпуск средств Build Tools. Если вы хотите использовать более раннюю версию средств Build Tools, которую можно было бы установить в контейнер позднее, следует сначала [создать](create-an-offline-installation-of-visual-studio.md) и [подготовить](update-a-network-installation-of-visual-studio.md) макет.

## <a name="install-script"></a>Скрипт установки

Чтобы производить сбор журналов при ошибке установки, создайте в рабочем каталоге пакетный скрипт с именем Install.cmd и следующим содержимым:

```shell
@if not defined _echo echo off
setlocal enabledelayedexpansion

call %*
if "%ERRORLEVEL%"=="3010" (
    exit /b 0
) else (
    if not "%ERRORLEVEL%"=="0" (
        set ERR=%ERRORLEVEL%
        call C:\TEMP\collect.exe -zip:C:\vslogs.zip

        exit /b !ERR!
    )
)
```

## <a name="dockerfile"></a>Dockerfile

В рабочем каталоге создайте файл Dockerfile со следующим содержимым:

::: moniker range="vs-2017"

```dockerfile
# escape=`

# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:3eaa3ba18f45e6561f32d8dd927045413f1dd043d7d29fb581f5cb3c6f7d7481
ARG FROM_IMAGE=mcr.microsoft.com/dotnet/framework/sdk:4.7.2-windowsservercore-ltsc2019
FROM ${FROM_IMAGE}

# Copy our Install script.
COPY Install.cmd C:\TEMP\

# Download collect.exe in case of an install failure.
ADD https://aka.ms/vscollect.exe C:\TEMP\collect.exe

# Use the latest release channel. For more control, specify the location of an internal layout.
ARG CHANNEL_URL=https://aka.ms/vs/15/release/channel
ADD ${CHANNEL_URL} C:\TEMP\VisualStudio.chman

# Download and install Build Tools excluding workloads and components with known issues.
ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe
RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --installPath C:\BuildTools `
    --channelUri C:\TEMP\VisualStudio.chman `
    --installChannelUri C:\TEMP\VisualStudio.chman `
    --all `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
    --remove Microsoft.VisualStudio.Component.Windows81SDK

# Start developer command prompt with any other commands specified.
ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

# Default to PowerShell if no other command specified.
CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

   > [!WARNING]
   > Visual Studio 2017 версии 15.8 или более ранней (любого продукта) не будет правильно установлена на образ mcr\.microsoft\.com\/windows\/servercore:1809 или более поздней версии. При этом сообщение об ошибке не отображается.
   >
   > Дополнительные сведения см. в статье об [известных проблемам с контейнерами](build-tools-container-issues.md).

::: moniker-end

::: moniker range="vs-2019"

```dockerfile
# escape=`

# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:324e9ab7262331ebb16a4100d0fb1cfb804395a766e3bb1806c62989d1fc1326
ARG FROM_IMAGE=mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019
FROM ${FROM_IMAGE}

# Copy our Install script.
COPY Install.cmd C:\TEMP\

# Download collect.exe in case of an install failure.
ADD https://aka.ms/vscollect.exe C:\TEMP\collect.exe

# Use the latest release channel. For more control, specify the location of an internal layout.
ARG CHANNEL_URL=https://aka.ms/vs/16/release/channel
ADD ${CHANNEL_URL} C:\TEMP\VisualStudio.chman

# Download and install Build Tools excluding workloads and components with known issues.
ADD https://aka.ms/vs/16/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe
RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --installPath C:\BuildTools `
    --channelUri C:\TEMP\VisualStudio.chman `
    --installChannelUri C:\TEMP\VisualStudio.chman `
    --all `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
    --remove Microsoft.VisualStudio.Component.Windows81SDK

# Start developer command prompt with any other commands specified.
ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

# Default to PowerShell if no other command specified.
CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

::: moniker-end

Выполните следующую команду, чтобы произвести сборку образа в текущем рабочем каталоге:

::: moniker range="vs-2017"

```shell
docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
```

::: moniker-end

::: moniker range="vs-2019"

```shell
docker build -t buildtools2019:16.0.28714.193 -t buildtools2019:latest -m 2GB .
```

::: moniker-end

При необходимости передайте оба аргумента `FROM_IMAGE` и `CHANNEL_URL` или один из них с помощью параметра командной строки `--build-arg`, чтобы указать другой базовый образ или другое расположение внутреннего макета для поддержания фиксированного образа.

## <a name="diagnosing-install-failures"></a>Диагностика ошибок установки

В этом примере скачиваются определенные средства и проверяется совпадение хэш-кодов. В нем также скачивается последняя версия служебной программы для сбора журналов Visual Studio и .NET, чтобы в случае сбоя установки вы могли скопировать журналы на хост-компьютер для анализа ошибок.

::: moniker range="vs-2017"

```shell
> docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
Sending build context to Docker daemon

...
Step 8/10 : RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache ...
 ---> Running in 4b62b4ce3a3c
The command 'cmd /S /C C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe ...' returned a non-zero code: 1603

> docker cp 4b62b4ce3a3c:C:\vslogs.zip "%TEMP%\vslogs.zip"
```

::: moniker-end

::: moniker range="vs-2019"

```shell
> docker build -t buildtools2019:16.0.28714.193 -t buildtools2019:latest -m 2GB .
Sending build context to Docker daemon

...
Step 8/10 : RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache ...
 ---> Running in 4b62b4ce3a3c
The command 'cmd /S /C C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe ...' returned a non-zero code: 1603

> docker cp 4b62b4ce3a3c:C:\vslogs.zip "%TEMP%\vslogs.zip"
```

::: moniker-end

Когда завершится выполнение последней строки, откройте файл %TEMP%\vslogs.zip на своем компьютере или отправьте сообщение об ошибке на веб-сайте [сообщества разработчиков](https://developercommunity.visualstudio.com).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Установка средств сборки в контейнер](build-tools-container.md)
* [Известные проблемы для контейнеров](build-tools-container-issues.md)
* [Идентификаторы рабочих нагрузок и компонентов для Visual Studio Build Tools](workload-component-id-vs-build-tools.md)
