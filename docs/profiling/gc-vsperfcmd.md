---
title: "Параметр GC (VSPerfCmd) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Параметр GC (VSPerfCmd)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

При использовании параметра **GC** включается сбор данных о выделении памяти .NET Framework и времени существования объекта.  Параметр **GC** может использоваться только с методом профилирования с выборкой и только с параметром **Launch**.  
  
 При использовании параметра **GC** команда VSPerfClrEnv **\/sampleon** не требуется.  
  
 Если дополнительные параметры не заданы или если задан параметр **Allocation**, собираются данные только о выделении памяти .NET Framework.  Если задан параметр **Lifetime**, собираются данные как о выделении памяти .NET Framework, так и о времени существования объектов .NET Framework.  
  
## Синтаксис  
  
```  
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]  
```  
  
#### Параметры  
 **Allocation**  
 По умолчанию.  Собирает данные об использовании времени и выделении памяти .NET Framework.  
  
 **Lifetime**  
 Собирает данные о выделении памяти .NET Framework и времени существования объектов .NET Framework.  
  
## Обязательные параметры  
 Параметр **GC** можно использовать только одновременно с параметром **Launch**.  
  
 **Launch:** `AppName`  
 Запускает заданное приложение и начинает профилирование с помощью метода выборки.  
  
## Пример  
 В следующем примере показан запуск приложения и сбор данных о выделении памяти .NET Framework.  
  
```  
VSPerfCmd.exe /Launch:TestApp.exe /gc  
```  
  
## См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб\-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Службы профилирования](../profiling/command-line-profiling-of-services.md)