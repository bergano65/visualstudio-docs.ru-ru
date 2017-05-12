---
title: "Недопустимый диапазон в наборе символов (JavaScript) | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5021"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Недопустимый диапазон в наборе символов (JavaScript)
Предпринята попытка создать регулярное выражение с недопустимым диапазоном набора символов.  Наборы символов должны состоять только из одиночных символов, таких как a\-z или 0\-9; в набор символов нельзя включать классы символов, такие как \\w.  Кроме того, первый символ в диапазоне должен располагаться перед вторым символом в диапазоне.  Примеры.  
  
```javascript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### Исправление ошибки  
  
-   Для составления набора символов регулярных выражений используйте только одиночные символы и следите, чтобы символы были расположены в правильном порядке.  
  
## См. также  
 [Объект Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ru-ru/ab0766e1-7037-45ed-aa23-706f58358c0e)