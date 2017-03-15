---
title: "Параметр AutoMark | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c4de965e-0364-4f78-9936-1f509e85df74
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Параметр AutoMark
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Параметр **AutoMark** задает количество миллисекунд между операциями сбора данных для событий программного счетчика производительности Windows.  Счетчики производительности Windows задаются параметром **WinCounter**.  
  
 В командной строке можно указать только один параметр **AutoMark**.  Обратите внимание, что интервал выборки **WinCounter**, заданный параметром **AutoMark**, не зависит от основного интервала выборки.  
  
## Синтаксис  
  
```  
VSPerfCmd.exe /Start:Method /WinCounter:Path /AutoMark:Milliseconds  
```  
  
#### Параметры  
 `Milliseconds`  
 Задает интервал времени \(в миллисекундах\) между операциями сбора данных для событий счетчика производительности Windows.  
  
## Обязательные параметры  
 **WinCounter:** `Path`  
 Задает счетчик производительности Windows, данные которого подлежат сбору.  При использовании метода инструментирования можно задать несколько счетчиков Windows.  При использовании метода выборки задать можно только один программный счетчик.  В командной строке, содержащий параметр **Start**, должен быть задан параметр **WinCounter**.  
  
## Пример  
 В этом примере устанавливается интервал выборки в 1000 миллисекунд для двух счетчиков производительности Windows.  
  
```  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /WinCounter:"\Process(*)\% Processor Time" /WinCounter:"\ASP.NET\Pages/sec" /AutoMark:1000  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб\-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Службы профилирования](../profiling/command-line-profiling-of-services.md)