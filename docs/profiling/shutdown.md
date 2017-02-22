---
title: "Shutdown | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Shutdown
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Параметр **Shutdown** обеспечивает выключение профилировщика и закрытие файла данных профилирования спустя определенное время ожидания после завершения или отсоединения профилируемого в данный момент процесса.  Параметр **Shutdown** должен быть последней командой сеанса профилирования.  
  
 Если параметр времени ожидания не задан, ожидание параметра **Shutdown** оказывается бесконечным.  Если параметр времени ожидания задан, этот параметр возвращается спустя заданное число секунд без выключения профилировщика или закрытия файла данных.  
  
 Параметр **Shutdown** должен быть единственным параметром, указанным в командной строке.  
  
## Синтаксис  
  
```  
VSPerfCmd.exe /Shutdown[:Timeout]  
```  
  
#### Параметры  
 `Timeout`  
 -   \(Необязательно.\) Если параметр времени ожидания задан, этот параметр возвращается спустя заданное число секунд без выключения профилировщика или закрытия файла данных профилирования.  
  
## См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб\-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Службы профилирования](../profiling/command-line-profiling-of-services.md)