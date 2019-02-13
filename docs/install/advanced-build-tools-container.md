---
title: Расширенный пример для контейнеров
description: ''
ms.date: 04/18/2018
ms.topic: conceptual
ms.assetid: e03835db-a616-41e6-b339-92b41d0cfc70
author: heaths
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 90969307d328519c95997be2ff0e8fad87fdc0a1
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55939805"
---
# <a name="advanced-example-for-containers"></a>Расширенный пример для контейнеров

Пример файла Dockerfile, приведенный в разделе [Установка средств сборки в контейнер](build-tools-container.md), всегда использует образ [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) на основе последней версии образа microsoft/windowsservercore и последнюю версию установщика Visual Studio Build Tools 2017. Если вы публикуете этот образ в [реестре Docker](https://azure.microsoft.com/services/container-registry), чтобы его могли извлекать другие пользователи, то во многих случаях он будет подходящим. Однако на практике чаще требуется использовать определенный базовый образ, скачивать определенные двоичные файлы и устанавливать определенные версии средств.

Приведенный ниже пример файла Dockerfile использует конкретный тег версии образа microsoft/dotnet-framework. Применение определенного тега для базового образа — распространенная практика. Таким образом вы не забудете, что для сборки или повторной сборки образов должна использоваться одна и та же основа.

> [!NOTE]
> Среду Visual Studio невозможно установить в образе microsoft/windowsservercore:10.0.14393.1593 или любом основанном на нем образе, так как в нем имеются известные проблемы с запуском установщика в контейнере. Дополнительные сведения см. в разделе [Известные проблемы](build-tools-container-issues.md).

В приведенном ниже примере скачивается последняя версия средств Build Tools 2017. Если вы хотите использовать более раннюю версию средств Build Tools, которую можно было бы установить в контейнер позднее, следует сначала [создать](create-an-offline-installation-of-visual-studio.md) и [подготовить](update-a-network-installation-of-visual-studio.md) макет.

## <a name="install-script"></a>Скрипт установки

Чтобы в случае ошибки происходил сбор данных журнала, создайте в рабочем каталоге пакетный скрипт с именем Install.cmd и следующим содержимым:

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

```dockerfile
# escape=`

# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:1a66e2b5f3a5b8b98ac703a8bfd4902ae60d307ed9842978df40dbc04ac86b1b
ARG FROM_IMAGE=microsoft/dotnet-framework:4.7.1-20180410-windowsservercore-1709
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
   > Visual Studio 2017 версии 15.8 или более ранней версии (любого продукта) не будет правильно установлена на образ mcr<span></span>.microsoft\.com\/windows\/servercore:1809 или более поздней версии. При этом сообщение об ошибке не отображается.
   >
   > Дополнительные сведения см. в статье об [известных проблемам с контейнерами](build-tools-container-issues.md).

Выполните следующую команду, чтобы произвести сборку образа в текущем рабочем каталоге:

```shell
docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
```

При необходимости передайте оба аргумента `FROM_IMAGE` и `CHANNEL_URL` или один из них с помощью параметра командной строки `--build-arg`, чтобы указать другой базовый образ или другое расположение внутреннего макета для поддержания фиксированного образа.

## <a name="diagnosing-install-failures"></a>Диагностика ошибок установки

В этом примере скачиваются определенные средства и проверяется совпадение хэш-кодов. В нем также скачивается последняя версия служебной программы для сбора журналов Visual Studio и .NET, чтобы в случае сбоя установки вы могли скопировать журналы на хост-компьютер для анализа ошибок.

```shell
> docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
Sending build context to Docker daemon
...
Step 8/10 : RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache ...
 ---> Running in 4b62b4ce3a3c
The command 'cmd /S /C C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe ...' returned a non-zero code: 1603

> docker cp 4b62b4ce3a3c:C:\vslogs.zip "%TEMP%\vslogs.zip"
```

Когда завершится выполнение последней строки, откройте файл %TEMP%\vslogs.zip на своем компьютере или отправьте сообщение об ошибке на веб-сайте [сообщества разработчиков](https://developercommunity.visualstudio.com).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Установка средств сборки в контейнер](build-tools-container.md)
* [Известные проблемы для контейнеров](build-tools-container-issues.md)
* [Идентификаторы рабочих нагрузок и компонентов для Visual Studio Build Tools 2017](workload-component-id-vs-build-tools.md)
