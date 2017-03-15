---
title: "Незапланированное волокно | Microsoft Docs"
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
  - "bc30948"
  - "vbc30948"
helpviewer_keywords: 
  - "BC30948"
ms.assetid: 982bf6d2-ce62-4451-8a23-82dacf8ee100
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Незапланированное волокно
Отладчик не может вычислить выражение, так как волокно его логики не запланировано в физическом потоке. Это происходит, если процесс выполняется в SQL Server с использованием волокон.  
  
 Волокно состоит из стека и контекста регистров, оно может выполняться в любом потоке. Волокно можно выгрузить из потока и перезапустить позже в другом потоке.  
  
 **Идентификатор ошибки:** BC30948  
  
### Исправление ошибки  
  
-   Убедитесь, что волокно запланировано в физическом потоке.  
  
## См. также  
 [Debugging SQL](http://msdn.microsoft.com/ru-ru/f27c17e6-1d90-49f2-9fc0-d02e6a27f109)   
 [Отладка в Visual Studio](../debugger/debugging-in-visual-studio.md)