---
title: "Метод setTime (Date) (JavaScript) | Microsoft Docs"
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
  - "setTime"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "SetTime - метод"
  - "time - метод"
ms.assetid: 86584748-7219-495b-bf56-e27f5782778c
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Метод setTime (Date) (JavaScript)
Задает значение даты и времени в объекте `Date`.  
  
## Синтаксис  
  
```  
  
dateObj.setTime(milliseconds)   
```  
  
## Параметры  
 `dateObj`  
 Обязательный.  Любой объект `Date`.  
  
 *milliseconds*  
 Обязательный.  Числовое значение, представляющее число миллисекунд, прошедших после полуночи 1 января, 1970 года \(время в формате GMT\).  
  
## Заметки  
 Если значение *milliseconds* является отрицательным, оно означает дату до 1970 года.  Диапазон доступных дат составляет приблизительно 285 616 лет до и после 1970 года.  
  
 Часовой пояс не имеет значения при установке даты и времени с помощью метода `setTime`.  
  
## Пример  
 В следующем примере показано использование метода `setTime`.  
  
```javascript  
function SetTimeTest(newtime){  
   var d, s;                  //Declare variables.  
   d = new Date();            //Create Date object.  
   d.setTime(newtime);        //Set time.  
   s = "Current setting is ";  
   s += d.toUTCString();  
   return(s);                 //Return new setting.  
}  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Относится к**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getTime \(Date\)](../../javascript/reference/gettime-method-date-javascript.md)