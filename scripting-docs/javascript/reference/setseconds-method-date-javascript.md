---
title: "Метод setSeconds (Date) (JavaScript) | Microsoft Docs"
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
  - "setSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "seconds - метод"
  - "setSeconds - метод"
ms.assetid: 986ffa54-1db6-4af2-ab8b-8353f64f0b57
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Метод setSeconds (Date) (JavaScript)
Устанавливает значение секунд в объекте `Date`, используя местное время.  
  
## Синтаксис  
  
```  
  
dateObj  
.setSeconds(  
numSeconds[, numMilli])   
```  
  
## Параметры  
 `dateObj`  
 Обязательный.  Любой объект `Date`.  
  
 *numSeconds*  
 Обязательный.  Числовое значение, равное количеству секунд.  
  
 `numMilli`  
 Необязательный.  Числовое значение, равное количеству миллисекунд.  
  
## Заметки  
 Все методы **set**, принимающие необязательные аргументы, в случае, когда необязательный аргумент не задан, используют значение, возвращаемое соответствующими методами **get**.  Например, если аргумент `numMilli` не задан, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] использует значение, возвращенное методом **getMilliseconds**.  
  
 Чтобы установить значение секунд с использованием универсального времени \(UTC\), используйте метод `setUTCSeconds`.  
  
 Если значение аргумента превышает верхнюю границу его диапазона или является отрицательным числом, остальные хранящиеся значения изменяются соответственно.  Например, если сохранена дата "5 января 1996 г., 00:00:00" и вызывается метод **setSeconds\(150\)**, дата принимает значение "5 января 1996 г., 00:02:30".  
  
 С помощью метода `setHours` можно задать часы, минуты, секунды и миллисекунды.  
  
## Пример  
 В следующем примере показано использование метода `setSeconds`.  
  
```javascript  
function SetSecondsDemo(nsec){  
   var d = new Date();         //Create Date object.  
   d.setSeconds(nsec);         //Set seconds.  
   var s = "Current setting is ";  
   s += d.toLocaleString();  
   return(s);                  //Return new setting.  
}  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Относится к**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getSeconds \(Date\)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [Метод getUTCSeconds \(Date\)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [Метод setUTCSeconds \(Date\)](../../javascript/reference/setutcseconds-method-date-javascript.md)