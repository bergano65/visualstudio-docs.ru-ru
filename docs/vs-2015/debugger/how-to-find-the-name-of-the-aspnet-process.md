---
title: Как найти имя процесса ASP.NET | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 53072013c1665687262d30f4a0c2720641c920be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685963"
---
# <a name="how-to-find-the-name-of-the-aspnet-process"></a>Практическое руководство. Поиск имени процесса ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Чтобы выполнить присоединение к выполняющемуся приложению [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], необходимо знать имя процесса [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]:  
  
- Если выполняется IIS 6.0 или IIS 7.0, процесс имеет имя w3wp.exe.  
  
- Если выполняется более ранняя версия IIS, то процесс имеет имя aspnet_wp.exe.  
  
  Для приложений, созданных с помощью [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] или более поздних версий, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] код может находиться в файловой системе и выполняться на тестовом сервере WebDev.WebServer.exe. В этом случае необходимо выполнить присоединение к WebDev.WebServer.exe вместо присоединения к процессу [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Этот скрипт применим только к локальной отладке.  
  
  Более ранние версии приложений ASP при внутрипроцессном выполнении выполняются в процессе inetinfo.exe.  
  
> [!NOTE]
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. [в разделе Настройка параметров разработки в Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-determine-whether-project-code-resides-on-the-file-system-or-iis"></a>Определение, размещен ли код проекта в файловой системе или IIS  
  
1. В Visual Studio откройте **Обозреватель решений** , если он еще не открыт.  
  
2. Выберите узел верхнего уровня, который содержит имя приложения.  
  
3. Если заголовок окна **свойств** содержит путь к файлу, код приложения находится в файловой системе.  
  
     В противном случае заголовок окна **Свойства** будет содержать имя веб-сайта.  
  
### <a name="to-determine-the-iis-version-under-which-the-application-is-running"></a>Определение версии IIS, в которой выполняется приложение  
  
1. Найдите **средства администрирования** и запустите их. В зависимости от операционной системы это может быть значок в **панели управления**или запись меню, которая появляется при нажатии кнопки **Пуск**.  
  
     В Windows XP **Панель управления** может находиться в представлении категорий или классическом представлении. В представлении по категориям необходимо нажать кнопку **переключиться на классический вид** или **производительность и обслуживание** , чтобы увидеть значок **средства администрирования** .  
  
2. В меню **Администрирование**выберите команду службы IIS. Появится диалоговое окно MMC.  
  
3. Если в левой области перечислены несколько компьютеров, выберите тот из них, на котором расположен код приложения.  
  
4. Версия IIS находится в столбце **версия** в правой области.  
  
## <a name="see-also"></a>См. также:  
 [Предварительные требования для удаленной отладки веб-приложений](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [Системные требования](../debugger/aspnet-debugging-system-requirements.md)   
 [Подготовка к отладке ASP.NET](../debugger/preparing-to-debug-aspnet.md)   
 [Отладка веб-приложений и скриптов](../debugger/debugging-web-applications-and-script.md)
