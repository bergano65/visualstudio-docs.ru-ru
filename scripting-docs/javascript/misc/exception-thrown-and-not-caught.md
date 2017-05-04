---
title: "Исключение сгенерировано, но не перехвачено | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5022"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Исключение сгенерировано, но не перехвачено
В код включен оператор `throw`, но он не входит в состав блока **try** или отсутствует связанный с ним блок **catch** для перехвата ошибки.  Исключения создаются внутри блока **try** с помощью оператора **throw** и перехватываются вне блока **try** с помощью оператора **catch**.  
  
### Исправление ошибки  
  
-   Поместите код, который может создать исключение, в блок **try** и убедитесь в наличии соответствующего блока **catch**.  
  
-   Убедитесь, что оператор catch ожидает правильную форму исключения.  
  
-   Если исключение создается заново, убедитесь в наличии другого соответствующего оператора catch.  
  
## См. также  
 [Объект Error](../../javascript/reference/error-object-javascript.md)   
 [Оператор throw](../../javascript/reference/throw-statement-javascript.md)   
 [Оператор try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)