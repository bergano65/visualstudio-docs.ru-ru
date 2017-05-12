---
title: "Ожидалось логическое значение | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5010"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Ожидалось логическое значение
Предпринята попытка вызова метода **Boolean.prototype.toString** или **Boolean.prototype.valueOf** для объекта, тип которого отличается от типа `Boolean`.  Объект вызова этого типа должен иметь тип `Boolean`.  Примеры.  
  
```javascript  
var o = new Object;  
o.f = Boolean.prototype.toString;  
o.f();  
```  
  
### Исправление ошибки  
  
-   Вызывайте методы **Boolean.prototype.toString** и **Boolean.prototype.valueOf** только для объектов типа **Boolean**.  
  
## См. также  
 [Объект Boolean](../../javascript/reference/boolean-object-javascript.md)   
 [Типы данных](../../javascript/data-types-javascript.md)   
 [Управление выполнением программы](../../javascript/controlling-program-flow-javascript.md)   
 [Копирование, передача и сравнение данных](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)