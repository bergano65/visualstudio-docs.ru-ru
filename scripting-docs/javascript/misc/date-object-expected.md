---
title: "Предполагается наличие объекта-даты | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5006"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Предполагается наличие объекта-даты
Предпринята попытка вызова метода **Date.prototype.toString** или **Date.prototype.valueOf** для объекта, тип которого отличается от типа `Date`.  Объект вызова этого типа должен иметь тип `Date`.  Примеры.  
  
```javascript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### Исправление ошибки  
  
-   Вызывайте методы **Date.prototype.toString** и **Date.prototype.valueOf** только для объектов типа `Date`.  
  
## См. также  
 [Объект Date](../../javascript/reference/date-object-javascript.md)   
 [Метод getDate \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Встроенные объекты](../../javascript/intrinsic-objects-javascript.md)