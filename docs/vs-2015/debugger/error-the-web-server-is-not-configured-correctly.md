---
title: 'Ошибка: неправильно настроен веб-сервер | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3cfbcf127b9951ddfce1d3db8fe1177087b0350a
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918503"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Ошибка: неправильно настроен веб-сервер
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Возможные причины этой ошибки:  
  
- Попытка выполнить отладку веб-приложения .NET, которое было скопировано на другой компьютер, переименовано вручную или удалено.  
  
- Недостаточное число соединений со службами IIS. Более подробную информацию о развертывании веб-сайта в службах IIS см. в статье [Создание веб-сайта](/iis/get-started/getting-started-with-iis/create-a-web-site).  
  
- Если вы пытаетесь отладить приложение ASP.NET, обратитесь к статье [Публикация в службах IIS](https://docs.asp.net/en/latest/publishing/iis.html) за инструкциями по развертыванию на удаленном компьютере со службами IIS 8 или более поздней версии либо к разделу [Remote Debugging ASP.NET on a Remote IIS 7.5 Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) за инструкциями по развертыванию на удаленном компьютере со службами IIS 7.5.  
  
## <a name="see-also"></a>См. также раздел  
 [Отладка веб-приложений: ошибки и устранение неполадок](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
