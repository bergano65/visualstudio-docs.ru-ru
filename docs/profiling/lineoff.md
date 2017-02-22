---
title: "LineOff | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# LineOff
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

При использовании метода профилирования с выборкой профилировщик по умолчанию собирает сведения о количестве строк исходного кода и данные о смещении номеров строк.  Параметр **LineOff** команды VSPerfCmd отключает сбор данных о номерах строк, когда команда VSPerfCmd используется для запуска приложения.  Если задан параметр **LineOff**, данные профилирования собираются до уровня функции.  
  
 Параметр **LineOff** может использоваться только с параметром **Launch** и только в том случае, если профилировщик был инициализирован для выборки с помощью параметра **Start**:**Sample**.  
  
## Синтаксис  
  
```  
VSPerfCmd.exe /Launch:AppName /LineOff [Options]  
```  
  
#### Параметры  
 Нет  
  
## Обязательные параметры  
 Параметр **LineOff** можно использовать только в команде, в которой также содержится параметр **Launch**.  
  
 **Launch:** `AppName`  
 Запускает заданное приложение и начинает профилирование с помощью метода выборки.  
  
## Пример  
 Следующий пример запускает приложение и профилировщик, отключая выборку на уровне строк.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /LineOff  
```  
  
## См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб\-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Службы профилирования](../profiling/command-line-profiling-of-services.md)