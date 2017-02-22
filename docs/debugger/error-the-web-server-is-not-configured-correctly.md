---
title: "Ошибка: неправильно настроен веб-сервер | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.remote.projnotconfigured"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "отладчик, ошибки веб-приложения"
ms.assetid: 875ba87f-c372-4126-8fe3-e33931cf26c0
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Ошибка: неправильно настроен веб-сервер
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Возможные причины этой ошибки:  
  
-   Попытка выполнить отладку веб\-приложения .NET, которое было скопировано на другой компьютер, переименовано вручную или удалено.  
  
-   Недостаточное число соединений со службами IIS. Более подробную информацию о развертывании веб\-сайта в службах IIS см. в статье [Создание веб\-сайта](http://www.iis.net/learn/get-started/getting-started-with-iis/create-a-web-site).  
  
-   Если вы пытаетесь отладить приложение ASP.NET, обратитесь к статье [Публикация в службах IIS](https://docs.asp.net/en/latest/publishing/iis.html) за инструкциями по развертыванию на удаленном компьютере со службами IIS 8 или более поздней версии либо к разделу [Удаленная отладка ASP.NET на удаленном компьютере IIS 7.5](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) за инструкциями по развертыванию на удаленном компьютере со службами IIS 7.5.  
  
## См. также  
 [Отладка веб\-приложений: ошибки и устранение неполадок](../debugger/debugging-web-applications-errors-and-troubleshooting.md)