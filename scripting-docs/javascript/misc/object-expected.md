---
title: "Предполагается наличие объекта | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5007"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 5d88c93d-e5b5-4b11-9bb5-bf1a5e41ccc3
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Предполагается наличие объекта
Предпринята попытка вызвать метод или свойство для объекта, тип которого отличается от типа `Object`, или передать аргумент, тип которого отличается от типа `Object`. Объект вызова этого типа должен иметь тип `Object`.  
  
### Исправление ошибки  
  
-   Вызывайте этот метод или свойство только для объектов типа `Object`.  
  
-   Если ошибка связана с аргументом без объектов, передайте объект типа `Object`.  
  
-   Проверьте, не вызывается ли вместо объекта типа `Object` неопределенная или пустая ссылка.  
  
     Такая ошибка возникает, например, в связи с аргументом myVar, указанном в следующем коде:  
  
    ```javascript  
    var str = myVar.toString();  
    ```  
  
     Вместо него можно использовать следующий код:  
  
    ```javascript  
    if (myVar) {  
        var str = myVar.toString();  
    }  
    ```  
  
## См. также  
 [Объект Object](../../javascript/reference/object-object-javascript.md)   
 [Объекты и массивы](../../javascript/objects-and-arrays-javascript.md)