---
title: "Ожидалась строка | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5005"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 4c214c4b-9cd7-473b-8d90-2344c0375c25
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Ожидалась строка
Предпринята попытка вызова метода **String.prototype.toString** или **String.prototype.valueOf** для объекта, тип которого отличается от типа `String`.  Объект вызова этого типа должен иметь тип `String`.  
  
### Исправление ошибки  
  
-   Вызывайте методы **String.prototype.toString** и **String.prototype.valueOf** только для объектов типа `String`.  
  
## См. также  
 [Объект String](../../javascript/reference/string-object-javascript.md)   
 [Метод toString \(Object\)](../../javascript/reference/tostring-method-object-javascript.md)