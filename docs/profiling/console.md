---
title: "Параметр Console | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Параметр Console
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Параметр **Console** программы VSPerfCmd.exe запускает указанное приложение в новом окне командной строки.  Параметр **Console** можно использовать только одновременно с параметром VSPerfCmd **Launch**.  Если приложение не является приложением командной строки, параметр **Console** ни на что не влияет.  
  
## Синтаксис  
  
```  
VSPerfCmd.exe /Launch:AppName /Console  
```  
  
#### Параметры  
 Нет  
  
## Обязательные параметры  
 Параметр **Console** можно задавать только в командной строке, в которой также содержится параметр **Launch**.  
  
 **Launch:** `AppName`  
 Запускает профилировщик для приложения, заданного параметром `AppName`.  
  
## См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб\-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Службы профилирования](../profiling/command-line-profiling-of-services.md)