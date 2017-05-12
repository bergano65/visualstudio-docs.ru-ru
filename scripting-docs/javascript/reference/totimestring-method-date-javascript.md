---
title: "Метод toTimeString (Date) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "toTimeString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toTimeString - метод"
ms.assetid: a4a8c0f2-55a9-4e84-94c3-f0a547fb04b5
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Метод toTimeString (Date) (JavaScript)
Возвращает время в виде строкового значения.  
  
## Синтаксис  
  
```  
  
objDate. toTimeString( )  
```  
  
## Заметки  
 Обязательная ссылка `objDate` — это объект `Date`.  
  
 Метод `toTimeString` возвращает строковое значение, содержащее время в текущем часовом поясе.  
  
## Пример  
 В следующем примере устанавливается время, равное 2000 миллисекунд после полуночи 1\-го января 1970 в формате UTC, затем это значение записывается в документ.  
  
```javascript  
var aDate = new Date();  
     aDate.setTime(2000);  
     document.write(aDate.toTimeString());  
  
// Output depends on the time in the current time zone.  
  
```  
  
## Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## См. также  
 [Метод toDateString \(Date\)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [Метод toLocaleTimeString \(Date\)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)