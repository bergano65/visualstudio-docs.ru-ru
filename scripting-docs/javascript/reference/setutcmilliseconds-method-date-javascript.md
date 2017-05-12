---
title: "Метод setUTCMilliseconds (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "даты, время в формате UTC"
  - "миллисекунды"
  - "setUTCMilliseconds - метод"
  - "время в формате UTC, параметр"
ms.assetid: ed8e4486-d4b2-4b73-836b-dd1d3bb991a0
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Метод setUTCMilliseconds (Date) (JavaScript)
Устанавливает значение миллисекунд в объекте `Date`, используя универсальное время UTC.  
  
## Синтаксис  
  
```  
  
dateObj.setUTCMilliseconds(numMilli)   
```  
  
## Параметры  
 `dateObj`  
 Обязательный.  Любой объект `Date`.  
  
 `numMilli`  
 Обязательный.  Числовое значение, равное количеству миллисекунд.  
  
## Заметки  
 Чтобы установить значение миллисекунд с использованием местного времени, используйте метод `setMilliseconds`.  
  
 Если значение аргумента `numMilli` превышает 999 или является отрицательным числом, хранящееся значение секунд \(а при необходимости минут, часов и т. д.\) увеличивается соответствующим образом.  
  
## Пример  
 В следующем примере показано использование метода `setUTCMilliseconds`.  
  
```javascript  
function SetUTCMSecDemo(nmsec){     
// Create Date object.  
   var d = new Date();             
// Set UTC milliseconds.  
   d.setUTCMilliseconds(nmsec);    
  
   var s = "Current setting is ";  
   s += d.toUTCString();  
   s += " and " + d.getUTCMilliseconds();  
   s += " milliseconds"  
   return(s);  
}  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Относится к**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getMilliseconds \(Date\)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [Метод getUTCMilliseconds \(Date\)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [Метод setMilliseconds \(Date\)](../../javascript/reference/setmilliseconds-method-date-javascript.md)