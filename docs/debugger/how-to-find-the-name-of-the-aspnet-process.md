---
title: Поиск выполняющегося процесса ASP.NET | Документация Майкрософт
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
ms.openlocfilehash: 54aa98dd238d7a78e4ae89af05dceae0f9911478
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187658"
---
# <a name="find-the-name-of-the-aspnet-process"></a>Поиск имени процесса ASP.NET

Чтобы выполнить отладку выполняющегося [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] приложения, отладчик Visual Studio должен присоединиться к [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] процессу по имени.

**Чтобы узнать, какой процесс выполняет приложение ASP.NET:**

1. При запуске приложения в Visual Studio выберите **отладка** > **присоединить к процессу**.

1. В диалоговом окне **Присоединение к процессу** введите первые буквы имен процессов из следующего списка или введите их в поле поиска. На нем работает приложение ASP.NET. Подключитесь к этому процессу, чтобы выполнить отладку приложения.

    - *w3wp. exe* — это IIS 6,0 и более поздние версии.
    - *aspnet_wp. exe* — более ранние версии IIS.
    - *iisexpress. exe* — iisexpress.
    - *файл DotNet. exe* ASP.NET Core.
    - *Inetinfo. exe* — это старые приложения ASP, выполняющиеся в процессе.

>[!NOTE]
>Visual Studio 2012 и более ранние [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] код может находиться в файловой системе и выполняться на тестовом сервере *WebDev.* WebTest. exe или *WebDev. WebServer40. exe*. В этом случае для локальной отладки подключитесь к *WebDev.* WebDev. exe или *. WebServer40. exe* , а не к процессу [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

**См. также:**

- [Присоединение к выполняемому процессу](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Необходимые условия для удаленной отладки веб-приложений](remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Требования к системе](../debugger/aspnet-debugging-system-requirements.md)
- [Отладка приложений ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)