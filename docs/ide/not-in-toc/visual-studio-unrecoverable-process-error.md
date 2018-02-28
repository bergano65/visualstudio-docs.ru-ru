---
title: "Неустранимая ошибка процесса в Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 02/23/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editor
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 703e27a95d6a0f4b680ad6a729dc974dfe98fc11
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/04/2018
---
# Неустранимая ошибка процесса в Visual Studio

В Visual Studio 2017 применяется несколько внепроцессных процессов для выполнения необходимых фоновых задач, таких как динамическое модульное тестирование, анализаторы кода и т. д. Эти процессы выполняются вне процесса для предоставления Visual Studio преимуществ производительности, таких как быстрое реагирование при выполнении ресурсоемких и продолжительных заданий. Кроме того, так как Visual Studio является 32-разрядным процессом, внепроцессный запуск процессов позволяет выделять операциям с интенсивным использованием памяти область памяти большего объема.

Если какой-либо из этих процессов по какой-то причине завершает работу, отображается всплывающая строка с сообщением об ошибке:

"К сожалению, произошла неустранимая ошибка процесса, используемого Visual Studio. Рекомендуется сохранить работу, а затем закрыть и перезапустить Visual Studio".

Если вы видите это сообщение, необходимо немедленно сохранить работу и затем закрыть и перезапустить Visual Studio. Если этого не сделать, в любой момент может произойти сбой Visual Studio.

## Список процессов

Ниже приведен список используемых в Visual Studio внепроцессных процессов, которые должны быть запущены для обеспечения правильной работы Visual Studio.

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
