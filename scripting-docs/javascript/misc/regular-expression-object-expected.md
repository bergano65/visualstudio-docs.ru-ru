---
title: "Предполагается наличие объекта регулярного выражения | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5016"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: e226096c-c58f-4bcb-a71e-fa32ce474b67
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Предполагается наличие объекта регулярного выражения
Предпринята попытка вызова метода **RegExp.prototype.toString** или **RegExp.prototype.valueOf** для объекта, тип которого отличается от типа `RegExp`.  Объект вызова этого типа должен иметь тип `RegExp`.  
  
### Исправление ошибки  
  
-   Вызывайте методы **RegExp.prototype.toString** и **RegExp.prototype.valueOf** только для объектов типа `RegExp`.  
  
## См. также  
 [Объект Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ru-ru/ab0766e1-7037-45ed-aa23-706f58358c0e)