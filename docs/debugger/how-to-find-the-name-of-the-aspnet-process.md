---
title: Найти запущенный процесс ASP.NET | Документация Майкрософт
ms.date: 11/04/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 27221a4ae47b9fb06130b550ceb6d3cc1f00dce0
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56680962"
---
# <a name="find-the-name-of-the-aspnet-process"></a>Поиск имени процесса ASP.NET

Для отладки запущенной [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] приложения, необходимо присоединить отладчик Visual Studio к [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] процесса по имени.

**Чтобы узнать, какой процесс выполняется в приложении ASP.NET:**

1. С помощью приложения, выполняемого в Visual Studio, выберите **Отладка** > **присоединение к процессу**.

1. В **присоединение к процессу** диалоговое окно, введите первые буквы процесса имена из следующего списка, или в поле поиска введите. Тот, который выполняется та же выполнение приложения ASP.NET. Присоедините к процессу отладки приложения.

    - *w3wp.exe* — IIS 6.0 и более поздних версий.
    - *aspnet_wp.exe* является более ранних версий IIS.
    - *iisexpress.exe* — IISExpress.
    - *DotNet.exe* — ASP.NET Core.
    - *Inetinfo.exe* является внутренним старые приложения ASP.

>[!NOTE]
>Visual Studio 2012 и ранее [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] кода можно в файловой системе и выполните на тестовом сервере *WebDev.WebServer.exe* или *WebDev.WebServer40.exe*. В этом случае для локальной отладки, присоединить к *WebDev.WebServer.exe* или *WebDev.WebServer40.exe* вместо [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] процесса.

**См. также:**

- [Присоединение к выполняемому процессу](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Необходимые условия для удаленной отладки веб-приложений](/visualstudio/debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer)
- [Требования к системе](../debugger/aspnet-debugging-system-requirements.md)
- [Отладка приложений ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)