---
title: "Метод toUTCString (Date) (JavaScript) | Microsoft Docs"
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
  - "toUTCString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toUTCString - метод"
  - "даты в формате UTC, преобразование в строки"
ms.assetid: eb0983ed-7884-42fa-a2cc-de92b3111207
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Метод toUTCString (Date) (JavaScript)
Возвращает дату, преобразованную в строку с использованием универсального времени UTC.  
  
## Синтаксис  
  
```  
  
dateObj.toUTCString()   
```  
  
## Заметки  
 Обязательная ссылка `dateObj` — это любой объект `Date`.  
  
 Метод `toUTCString` возвращает объект `String`, содержащий дату в формате UTC в удобной и понятной форме.  
  
## Пример  
 В следующем примере показано использование метода `toUTCString`.  
  
```javascript  
function toUTCStrDemo(){  
   var d, s;                   //Declare variables.  
   d = new Date();             //Create Date object.  
   s = "Current setting is ";  
   s += d.toUTCString();       //Convert to UTC string.  
   return(s);                  //Return UTC string.  
}  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Относится к**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод toGMTString \(Date\)](../../javascript/reference/togmtstring-method-date-javascript.md)