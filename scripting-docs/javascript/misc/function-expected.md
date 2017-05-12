---
title: "Ожидалась функция | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5002"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: f62ade94-9f6f-4832-9b9b-49a06a385bbe
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Ожидалась функция
Предпринята попытка вызова одного из методов **прототипа функции** для объекта, который не был объектом `Function`, или в контексте вызова функции использован объект.  Например, следующий код вызывает эту ошибку, поскольку **example** не является функцией.  
  
```javascript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### Исправление ошибки  
  
-   Вызывайте методы **прототипа функции** только для объектов `Function`.  
  
-   Следите, чтобы оператор вызова функции `()` использовался только для вызова функций.  
  
## См. также  
 [Объект Function](../../javascript/reference/function-object-javascript.md)   
 [Свойство prototype \(Object\)](../../javascript/reference/prototype-property-object-javascript.md)