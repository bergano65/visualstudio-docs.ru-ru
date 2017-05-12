---
title: "Метод setMilliseconds (Date) (JavaScript) | Microsoft Docs"
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
  - "setMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "миллисекунды"
  - "setMilliseconds - метод"
ms.assetid: 6c398961-130e-4f60-802f-6c30e1ef4de4
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Метод setMilliseconds (Date) (JavaScript)
Устанавливает значение миллисекунд в объекте `Date`, используя локальное время.  
  
## Синтаксис  
  
```  
  
dateObj.  
setMilliseconds(  
numMilli  
)   
```  
  
## Параметры  
 `dateObj`  
 Обязательный.  Любой объект `Date`.  
  
 `numMilli`  
 Обязательный.  Числовое значение, равное количеству миллисекунд.  
  
## Заметки  
 Чтобы установить значение миллисекунд с использованием универсального времени \(UTC\), используйте метод `setUTCMilliseconds`.  
  
 Если значение аргумента `numMilli` превышает 999 или является отрицательным числом, хранящееся значение секунд \(а при необходимости минут, часов и т. д.\) увеличивается соответствующим образом.  
  
## Пример  
 В следующем примере показано использование метода `setMilliseconds`.  
  
```javascript  
function SetMSecDemo(nmsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setMilliseconds(nmsec);    // Set milliseconds.  
   s = "Current setting is ";  
   s += d.toLocaleString();  
   s += " and " + d.getMilliseconds();  
   s += " milliseconds";  
   return(s);                   // Return new date setting.  
}  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Относится к**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getMilliseconds \(Date\)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [Метод getUTCMilliseconds \(Date\)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [Метод setUTCMilliseconds \(Date\)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)