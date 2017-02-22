---
title: "Output | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Output
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Параметр **Output** задает имя и файла данных профилирования для сеанса профилирования.  Параметр **Output** должен использоваться с параметром **Start**.  
  
## Синтаксис  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### Параметры  
 `FileName`  
 Имя файла данных.  Можно задавать как полный, так и частичный путь.  Если путь не указан, файл создается в текущем каталоге.  
  
## Обязательные параметры  
 Параметр **Output** используется с параметром **Start**.  
  
 **Start:** `Method`  
 Задает имя выходного файла.  
  
## Пример  
 В следующем примере файл данных профилирования создается в текущем каталоге.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
```  
  
## См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб\-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Службы профилирования](../profiling/command-line-profiling-of-services.md)