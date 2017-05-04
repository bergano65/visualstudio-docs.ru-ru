---
title: "Ожидался объект &quot;перечисление&quot; | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5015"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Ожидался объект &quot;перечисление&quot;
Предпринята попытка вызова метода **Enumerator.prototype.atEnd, Enumerator.prototype.item, Enumerator.prototype.moveFirst** или **Enumerator.prototype.moveNext** для объекта, не имеющего тип `Enumerator`.  Объект вызова этого типа должен иметь тип `Enumerator`.  Ниже приведен пример кода, который нарушает это правило.  
  
```javascript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### Исправление ошибки  
  
-   Вызывайте методы **Enumerator.prototype.atEnd**, **Enumerator.prototype.item**, **Enumerator.prototype.moveFirst** и **Enumerator.prototype.moveNext** только для объектов типа `Enumerator`.  Чтобы выяснить, является ли объект объектом `Enumerator`, используйте:  
  
    ```  
    if(x instanceof Enumerator)  
    ```  
  
## См. также  
 [Объект Enumerator](../../javascript/reference/enumerator-object-javascript.md)