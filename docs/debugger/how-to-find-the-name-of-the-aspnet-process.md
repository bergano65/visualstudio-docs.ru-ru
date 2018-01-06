---
title: "Как: поиск имени процесса ASP.NET | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
caps.latest.revision: "29"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: aspnet
ms.openlocfilehash: e542e58bab483a1f20029bb66a073ae07d45afba
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-find-the-name-of-the-aspnet-process"></a>Практическое руководство. Поиск имени процесса ASP.NET
Чтобы выполнить присоединение к выполняющемуся приложению [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], необходимо знать имя процесса [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]:  

-   При использовании ASP.NET Core в IIS или IISExpress имя процесса является dotnet.exe.

-   Если вы используете ASP.NET в IIS 6.0 позже, процесс имеет имя w3wp.exe.  
  
-   При использовании ASP.NET на более ранней версии IIS имеет имя aspnet_wp.exe.

-   При использовании ASP.NET в IISExpress называется iisexpress.exe.
  
Для приложений, построенных с помощью версий Visual Studio до Visual Studio 2012 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] код может находятся в файловой системе и выполняться под управлением тестового сервера WebDev.WebServer.exe или WebDev.WebServer40.exe. В этом случае необходимо присоединить к WebDev.WebServer.exe или WebDev.WebServer40.exe вместо [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] процесса. Этот скрипт применим только к локальной отладке.
  
Более ранние версии приложений ASP при внутрипроцессном выполнении выполняются в процессе inetinfo.exe.  

### <a name="to-determine-the-iis-version-under-which-the-application-is-running"></a>Определение версии IIS, в которой выполняется приложение  

1.  Убедитесь, что приложения и затем из Visual Studio с помощью [присоединиться к процессу](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) команды.

2.  Введите имя процесса, такие как w3wp.exe для быстрого поиска процессов в первую букву **доступные процессы** списка.

    Доступные процессы из списка в этом разделе указывается, какие версии IIS доступны или процесса, в котором выполняется приложение.

    > [!NOTE]
    > Начиная с Visual Studio 2017 г., можно использовать поле поиска для поиска имени процесса.
  
## <a name="see-also"></a>См. также  
 [Присоединение к выполняемому процессу](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
 [Условия для удаленной отладки веб-приложений](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [Требования к системе для .NET Framework](../debugger/aspnet-debugging-system-requirements.md)   
 [Отладка приложений ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)