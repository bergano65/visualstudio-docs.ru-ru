---
title: "Параметр CrossSession | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Параметр CrossSession
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Параметр VSPerfCmd.exe **CrossSession** позволяет профилировщику собирать данные из любого консольного сеанса.  Параметр **CrossSession** используется с параметром **Start**.  
  
 Вместо **CrossSession** можно использовать сокращение **CS**.  
  
## Синтаксис  
  
```  
VSPerfCmd.exe /Start:Method /CrossSession [Options]  
```  
  
#### Параметры  
 Нет  
  
## Допустимые параметры  
 Для включения профилирования в рамках другого сеанса, необходимо указать параметр **CrossSession** с параметром **Start**.  **CrossSession** также необходимо указать в любой последующей команде **VSPerfCmd Attach** или **Detach**.  
  
 **Start:** `Method`  
 Параметр **Start** инициализирует профилировщик для заданного метода профилирования.  
  
 **Attach:** *PID*\[**,***PID*\]  
 Начинает профилирование указанного процесса.  
  
 **Detach**\[**:***PID*\[,*PID*\]\]  
 Останавливает профилирование указанного процесса.  
  
## Пример  
 В данном примере параметр **CrossSession** используется для присоединения к приложению, запущенному в другом консольном сеансе.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession  
VSPerfCmd.exe /Attach:12345 /CS  
```  
  
## См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб\-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Службы профилирования](../profiling/command-line-profiling-of-services.md)