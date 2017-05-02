---
title: "Метод setUTCHours (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCHours"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "даты, время в формате UTC"
  - "setUTCHours - метод"
  - "время в формате UTC, параметр"
ms.assetid: 257e36fd-fb06-4a4d-8634-d66a020a1511
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Метод setUTCHours (Date) (JavaScript)
Задает значение часов в объекте `Date`, используя время в формате UTC.  
  
## Синтаксис  
  
```  
  
dateObj.setUTCHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## Параметры  
 `dateObj`  
 Обязательный.  Любой объект `Date`.  
  
 `numHours`  
 Обязательный.  Числовое значение, равное количеству часов.  
  
 `numMin`  
 Необязательный.  Числовое значение, равное количеству минут.  Должен указываться, если используется аргумент `numSec` или аргумент `numMilli`.  
  
 `numSec`  
 Необязательный.  Числовое значение, равное количеству секунд.  Должен указываться, если используется аргумент `numMilli`.  
  
 `numMilli`  
 Необязательный.  Числовое значение, равное количеству миллисекунд.  
  
## Заметки  
 Все методы **set**, принимающие необязательные аргументы, в случае, когда необязательный аргумент не задан, используют значение, возвращаемое соответствующими методами **get**.  Например, если аргумент `numMin` не задан, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] использует значение, возвращенное методом `getUTCMinutes`.  
  
 Для задания значения часов с использованием местного времени используется метод `setHours`.  
  
 Если значение аргумента превышает верхнюю границу его диапазона или является отрицательным числом, остальные хранящиеся значения изменяются соответственно.  Например, если сохранена дата "00:00:00.00 5 января 1996 г." и вызывается метод **setUTCHours\(30\)**, дата принимает значение "06:00:00.00 6 января 1996 г".  
  
## Пример  
 В следующем примере показано использование метода `setUTCHours`.  
  
```javascript  
function SetUTCHoursDemo(nhr, nmin, nsec){     
   var d, s;                        // Declare variables.  
   d = new Date();                  // Create Date object.  
   d.setUTCHours(nhr, nmin, nsec);  // Set UTC hours, minutes, seconds.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                       // Return new setting.  
}  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Относится к**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getHours \(Date\)](../../javascript/reference/gethours-method-date-javascript.md)   
 [Метод getUTCHours \(Date\)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [Метод setHours \(Date\)](../../javascript/reference/sethours-method-date-javascript.md)