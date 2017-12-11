---
title: "Расширенный пример для контейнеров | Документы Майкрософт"
ms.custom: 
ms.date: 10/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e03835db-a616-41e6-b339-92b41d0cfc70
author: heaths
ms.author: heaths
manager: ghogen
ms.openlocfilehash: 8ab92d3936306ac47a59df33b4a1131341b28d44
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/22/2017
---
# <a name="advanced-example-for-containers"></a>Расширенный пример для контейнеров

Пример файла Dockerfile, приведенный в разделе [Установка средств сборки в контейнер](build-tools-container.md), всегда использует последние версии образа microsoft/windowsservercore и установщика Visual Studio Build Tools 2017. Если вы публикуете этот образ в [реестре Docker](https://azure.microsoft.com/services/container-registry), чтобы его могли извлекать другие пользователи, то во многих случаях он будет подходящим. Однако на практике чаще требуется использовать определенный базовый образ, скачивать определенные двоичные файлы и устанавливать определенные версии средств.

Приведенный ниже пример файла Dockerfile использует конкретный тег версии образа microsoft/windowsservercore. Применение определенного тега для базового образа — распространенная практика. Таким образом вы не забудете, что для сборки или повторной сборки образов должна использоваться одна и та же основа.

> [!NOTE]
> Среду Visual Studio невозможно установить в образе microsoft/windowsservercore:10.0.14393.1593, так как в нем имеются известные проблемы с запуском установщика в контейнере. Дополнительные сведения см. в разделе [Известные проблемы](build-tools-container-issues.md).

В примере также используется начальный загрузчик Build Tools 2017, который устанавливает определенную версию, созданную в одно время с начальным загрузчиком. Продукт все же можно обновить через канал выпуска, однако делать это для контейнеров, требующих повторной сборки, нецелесообразно. Чтобы узнать URL-адреса для определенного канала, можно скачать канал со страницы https://aka.ms/vs/15/release/channel, открыть файл JSON и найти в нем URL-адреса начального загрузчика. Дополнительные сведения см. в статье [Создание сетевой установки Visual Studio](create-a-network-installation-of-visual-studio.md).

```dockerfile
# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:d841bd78721c74f9b88e2700f5f3c2d66b54cb855b8acb4ab2c627a76a46301d
FROM microsoft/windowsservercore:10.0.14393.1770

# Use PowerShell commands to download, validate hashes, etc.
SHELL ["powershell.exe", "-ExecutionPolicy", "Bypass", "-Command", "$ErrorActionPreference='Stop'; $ProgressPreference='SilentlyContinue'; $VerbosePreference = 'Continue';"]

# Download Build Tools 15.4.27004.2005 and other useful tools.
ENV VS_BUILDTOOLS_URI=https://aka.ms/vs/15/release/6e8971476/vs_buildtools.exe \
    VS_BUILDTOOLS_SHA256=D482171C7F2872B6B9D29B116257C6102DBE6ABA481FAE4983659E7BF67C0F88 \
    NUGET_URI=https://dist.nuget.org/win-x86-commandline/v4.1.0/nuget.exe \
    NUGET_SHA256=4C1DE9B026E0C4AB087302FF75240885742C0FAA62BD2554F913BBE1F6CB63A0

# Download tools to C:\Bin and install Build Tools excluding workloads and components with known issues.
RUN New-Item -Path C:\Bin, C:\TEMP -Type Directory | Out-Null; \
    [System.Environment]::SetEnvironmentVariable('PATH', "\"${env:PATH};C:\Bin\"", 'Machine'); \
    function Fetch ([string] $Uri, [string] $Path, [string] $Hash) { \
      Invoke-RestMethod -Uri $Uri -OutFile $Path; \
      if ($Hash -and ((Get-FileHash -Path $Path -Algorithm SHA256).Hash -ne $Hash)) { \
        throw "\"Download hash for '$Path' incorrect\""; \
      } \
    }; \
    Fetch -Uri $env:NUGET_URI -Path C:\Bin\nuget.exe -Hash $env:NUGET_SHA256; \
    Fetch -Uri $env:VS_BUILDTOOLS_URI -Path C:\TEMP\vs_buildtools.exe -Hash $env:VS_BUILDTOOLS_SHA256; \
    Fetch -Uri 'https://aka.ms/vscollect.exe' -Path C:\TEMP\collect.exe; \
    $p = Start-Process -Wait -PassThru -FilePath C:\TEMP\vs_buildtools.exe -ArgumentList '--quiet --wait --norestart --nocache --installPath C:\BuildTools --all --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 --remove Microsoft.VisualStudio.Component.Windows81SDK'; \
    if (($ret = $p.ExitCode) -and ($ret -ne 3010)) { C:\TEMP\collect.exe; throw ('Install failed with exit code 0x{0:x}' -f $ret) }

# Restore default shell for Windows containers.
SHELL ["cmd.exe", "/s", "/c"]

# Start developer command prompt with any other commands specified.
ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

# Default to PowerShell if no other command specified.
CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

В этом примере скачиваются определенные средства и проверяется совпадение хэш-кодов. В нем также скачивается последняя версия служебной программы для сбора журналов Visual Studio и .NET, чтобы в случае сбоя установки вы могли скопировать журналы на хост-компьютер для анализа ошибок.

```shell
> docker build -t buildtools:15.4.27004.2005 -t buildtools:latest -m 2GB .
Sending build context to Docker daemon
...
Step 4/7 : RUN New-Item -Path C:\Bin, C:\TEMP -Type Directory | Out-Null; ...
 ---> Running in 4b62b4ce3a3c
Install failed with exit code 0x643
At line:1 char:1
+ throw ('Install failed with exit code 0x{0:x}' -f 1603)
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (Install failed with exit code 0x643:String) [], RuntimeException
    + FullyQualifiedErrorId : Install failed with exit code 0x643

> docker cp 4b62b4ce3a3c:C:\Users\ContainerAdministrator\AppData\Local\TEMP\vslogs.zip "%TEMP%\vslogs.zip"
```

Когда завершится выполнение последней строки, откройте файл %TEMP%\vslogs.zip на своем компьютере или отправьте сообщение об ошибке на веб-сайте [сообщества разработчиков](https://developercommunity.visualstudio.com).

## <a name="get-support"></a>Техническая поддержка
Иногда возникают проблемы. При сбое установки Visual Studio см. инструкции по [устранению неполадок и исправлению ошибок установки и обновления Visual Studio 2017](troubleshooting-installation-issues.md). Если описанные выше действия не устраняют проблему, вы можете обратиться к нам за помощью в чате в реальном времени (только на английском языке). Дополнительные сведения см. на [странице поддержки Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Ниже приведены несколько дополнительных вариантов:
* Вы можете сообщить о проблемах с продуктом в корпорацию Майкрософт, используя средство [Сообщить о проблеме](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Оно доступно как в Visual Studio Installer, так и в Visual Studio IDE.
* Вы можете оставить предложение о продукте на форуме [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Вы можете просматривать описания проблем в [сообществе разработчиков Visual Studio](https://developercommunity.visualstudio.com/). Там же можно получать ответы на интересующие вас вопросы.
* Вы также можете связаться с нами и другими разработчиками Visual Studio, используя [средство для обсуждения Visual Studio в сообществе Gitter](https://gitter.im/Microsoft/VisualStudio).  (Требуется учетная запись [GitHub](https://github.com/).)

## <a name="see-also"></a>См. также
* [Установка средств сборки в контейнер](build-tools-container.md)
* [Известные проблемы для контейнеров](build-tools-container-issues.md)
