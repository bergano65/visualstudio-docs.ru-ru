---
title: Процесс обнаружил неустранимую ошибку
ms.date: 06/22/2018
ms.topic: troubleshooting
helpviewer_keywords:
- unrecoverable error
- error, process
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: b6d69aa899ffea95c8da7c3513c6f7b0fa6002ee
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895162"
---
# <a name="visual-studio-unrecoverable-process-error"></a>Неустранимая ошибка процесса в Visual Studio

В Visual Studio 2017 применяется несколько внепроцессных процессов для выполнения необходимых фоновых задач, таких как динамическое модульное тестирование, анализаторы кода и т. д. Эти процессы выполняются вне процесса для предоставления Visual Studio преимуществ производительности, таких как быстрое реагирование при выполнении ресурсоемких и продолжительных заданий. Кроме того, так как Visual Studio является 32-разрядным процессом, внепроцессный запуск процессов позволяет выделять операциям с интенсивным использованием памяти область памяти большего объема.

Если процесс *ServiceHub.RoslynCodeAnalysisService.exe* или *ServiceHub.RoslynCodeAnalysisService32.exe* завершается по какой-либо причине, появляется всплывающая строка со следующим сообщением:

**"К сожалению, произошла неустранимая ошибка процесса, используемого Visual Studio. Рекомендуется сохранить работу, а затем закрыть и перезапустить Visual Studio".**

Если вы видите это сообщение, необходимо сохранить работу и затем закрыть и перезапустить Visual Studio.

## <a name="list-of-processes"></a>Список процессов

Ниже приведен список процессов вне процесса, используемый в Visual Studio. Этот список включает в себя процессы, запускающиеся в определенных рабочих процессах или сценариях, и поэтому в большинстве случаев не все они выполняются одновременно.

- Microsoft.Alm.Shared.Remoting.RemoteContainer.dll
- Microsoft.CodeAnalysis.LiveUnitTesting.EntryPoint
- PerfWatson2.exe
- ServiceHub.Host.Node.x86.exe
- ServiceHub.IdentityHost.exe
- ServiceHub.VSDetouredHost.exe
- ServiceHub.SettingsHost.exe
- ServiceHub.Host.CLR.x86.exe
- ServiceHub.RoslynCodeAnalysisService32.exe
- ServiceHub.RoslynCodeAnalysisService.exe
- WindowsAzureGuestAgent.exe
- WindowsAzureTelemetryService.exe
- WaAppAgent.exe

Если любой из этих процессов непредвиденно завершает работу, некоторые функциональные возможности в Visual Studio перестают работать. Для некоторых процессов потеря функциональности может быть незначительной. Другие процессы влияют на стабильность работы Visual Studio, и отображается сообщение об ошибке.