---
title: "Неопределенный идентификатор | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5009"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 8c8000d9-dd14-487e-922d-98430024a0f6
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Неопределенный идентификатор
Предпринята попытка использовать идентификатор, который компилятор [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] не распознает.  Значение undefined возвращается всегда, когда используется:  
  
-   переменная, которая не существует;  
  
-   переменная, которая была объявлена, но не имеет присвоенного значения;  
  
-   несуществующее свойство объекта.  
  
### Исправление ошибки  
  
-   Объявите переменную с помощью оператора **var** \(например, `var` x;\).  
  
## См. также  
 [Переменные](../../javascript/variables-javascript.md)   
 [Область действия переменных](../../javascript/advanced/variable-scope-javascript.md)