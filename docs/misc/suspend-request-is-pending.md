---
title: "Запрос на приостановку отложен | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30947"
  - "bc30947"
helpviewer_keywords: 
  - "BC30947"
ms.assetid: 6bc4df1b-e833-47c7-9568-9ced67a2af5d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Запрос на приостановку отложен
В отладчике Visual Studio выражение задает вызов процедуры, но есть запрос на приостановку потока.  
  
 Отладчик не будет пытаться вызвать процедуру в неактивном потоке.  
  
 **Идентификатор ошибки:** BC30947  
  
### Исправление ошибки  
  
-   По возможности определите источник запроса на приостановку потока, чтобы можно было предотвратить его дальнейшие вызовы.  
  
-   Завершите и перезапустите отладку.  
  
## См. также  
 [Отладка в Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [How to: Start Execution](http://msdn.microsoft.com/ru-ru/b0fe0ce5-900e-421f-a4c6-aa44ddae453c)   
 [How to: Stop Debugging or Stop Execution](http://msdn.microsoft.com/ru-ru/03c68f95-aa96-481b-990e-467e065453a5)   
 [Code Stepping Overview](http://msdn.microsoft.com/ru-ru/8791dac9-64d1-4bb9-b59e-8d59af1833f9)   
 [Выражения в Visual Basic](../Topic/Expressions%20in%20Visual%20Basic.md)