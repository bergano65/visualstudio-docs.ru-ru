---
title: "WinCounter | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# WinCounter
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Параметр **WinCounter** задает счетчик производительности Windows или приложения, данные которого собираются через заданные интервалы в процессе запуска профилирования.  Счетчики производительности Windows и приложений перечисляются в виде меток в файле данных профилирования.  Можно задать несколько счетчиков производительности, данные которых необходимо собирать, воспользовавшись отдельными параметрами.  
  
 По умолчанию данные счетчиков собираются каждые 500 миллисекунд.  С помощью параметра **AutoMark** можно задать другой интервал сбора данных.  
  
 Используется только один параметр **AutoMark**.  Если указаны несколько параметров **AutoMark**, используется последний из них.  
  
 Параметр **WinCounter** можно использовать только одновременно с параметром **Start**.  
  
## Синтаксис  
  
```  
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]  
```  
  
#### Параметры  
 `Path`  
 Счетчик производительности Windows в формате пути счетчика PDH.  
  
## Обязательные параметры  
 Параметр **WinCounter** можно использовать только одновременно с параметром **Start**.  
  
 **Start:** `Method`  
 Параметр **Start** инициализирует профилировщик для заданного метода профилирования.  
  
## Монопольные параметры  
 Параметр **AutoMark** можно использовать только одновременно с параметром **WinCounter**.  
  
 **AutoMark:** `Milliseconds`  
 Задает интервал времени \(в миллисекундах\) между сбором данных счетчика производительности Windows.  
  
## Пример  
 В следующем примере задан сбор данных с двух счетчиков производительности Windows с интервалом 1000 миллисекунд.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000  
```  
  
## См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб\-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Службы профилирования](../profiling/command-line-profiling-of-services.md)