---
title: "Ожидалось число | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5001"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b272f51a-97c2-4398-8b46-9cc49a5c0bd6
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Ожидалось число
Предпринята попытка вызова метода **Number.prototype.toString** или **Number.prototype.valueOf** для объекта, тип которого отличается от типа **Number**.  Объект вызова этого типа должен иметь тип **Number**.  
  
### Исправление ошибки  
  
-   Вызывайте методы **Number.prototype.toString** и **Number.prototype.valueOf** только для объектов типа **Number**.  
  
## См. также  
 [Объект Number](../../javascript/reference/number-object-javascript.md)   
 [Свойство number \(Error\)](../../javascript/reference/number-property-error-javascript.md)