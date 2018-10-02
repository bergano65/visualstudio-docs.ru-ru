---
title: 'Ошибка: Веб-сервер настроен правильно | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.remote.projnotconfigured
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 875ba87f-c372-4126-8fe3-e33931cf26c0
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 82d827e0f821712306cf1ec6049129fbf4437d67
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572034"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Ошибка: неправильно настроен веб-сервер
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [ошибка: веб-сервер настроен правильно](https://docs.microsoft.com/visualstudio/debugger/error-the-web-server-is-not-configured-correctly).  
  
Возможные причины этой ошибки:  
  
-   Попытка выполнить отладку веб-приложения .NET, которое было скопировано на другой компьютер, переименовано вручную или удалено.  
  
-   Недостаточное число соединений со службами IIS. Более подробную информацию о развертывании веб-сайта в службах IIS см. в статье [Создание веб-сайта](http://www.iis.net/learn/get-started/getting-started-with-iis/create-a-web-site).  
  
-   Если вы пытаетесь отладить приложение ASP.NET, ознакомьтесь с разделом [публикация в службах IIS](https://docs.asp.net/en/latest/publishing/iis.html) инструкции по развертыванию на удаленный компьютер, на котором запущены службы IIS 8 или более поздней версии, или [Remote Debugging ASP.NET on a Remote IIS 7.5 Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) инструкции по развертыванию на удаленном компьютере под управлением IIS 7.5.  
  
## <a name="see-also"></a>См. также  
 [Отладка веб-приложений: ошибки и устранение неполадок](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



