---
title: "throw требует после себя выражение на той же строке | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1035"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b03b7747-01a1-40c6-af80-a1dd70bc5781
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# throw требует после себя выражение на той же строке
Использовано ключевое слово `throw`, но после него в этой же строке кода не указано выражение.  Оператор `throw` состоит из двух частей: ключевого слова `throw` и следующего за ним выражения, которое будет вызвано.  Примеры.  
  
```javascript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Эти два компонента не должны разделяться.  
  
### Исправление ошибки  
  
-   Убедитесь, что ключевое слово `throw` и вызываемое выражение находятся в одной строке.  
  
## См. также  
 [Объект Error](../../javascript/reference/error-object-javascript.md)   
 [Оператор throw](../../javascript/reference/throw-statement-javascript.md)   
 [Оператор try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)