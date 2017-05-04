---
title: "Метод setHours (Date) (JavaScript) | Microsoft Docs"
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
  - "setHours"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "даты, параметр"
  - "часы"
  - "setHours - метод"
ms.assetid: 460f742d-f8d2-4874-9d07-2fb969fef066
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Метод setHours (Date) (JavaScript)
Устанавливает значение часа в объекте `Date`, используя локальное время.  
  
## Синтаксис  
  
```  
  
dateObj.setHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## Параметры  
 `dateObj`  
 Обязательный.  Любой объект `Date`.  
  
 `numHours`  
 Обязательный.  Числовое значение, равное количеству часов.  
  
 `numMin`  
 Необязательный.  Числовое значение, равное количеству минут.  Должен указываться, если используется какой\-либо из следующих аргументов.  
  
 `numSec`  
 Необязательный.  Числовое значение, равное количеству секунд.  Должен указываться, если используется следующий аргумент.  
  
 `numMilli`  
 Необязательный.  Числовое значение, равное количеству миллисекунд.  
  
## Заметки  
 Все методы **set**, принимающие необязательные аргументы, в случае, когда необязательный аргумент не задан, используют значение, возвращаемое соответствующими методами **get**.  Например, если аргумент `numMinutes` не задан, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] использует значение, возвращенное методом `getMinutes`.  
  
 Чтобы установить значение часа с использованием универсального времени \(UTC\), используйте метод `setUTCHours`.  
  
 Если значение аргумента превышает верхнюю границу его диапазона или является отрицательным числом, остальные хранящиеся значения изменяются соответственно.  Например, если сохранена дата "00:00:00 5 января 1996 г." и вызывается метод **setHours\(30\)**, то дата принимает значение "06:00:00 6 января 1996 г". Отрицательные числа ведут себя аналогично.  
  
## Пример  
 В следующем примере показано использование метода `setHours`.  
  
```javascript  
function SetHoursDemo(nhr, nmin, nsec){  
   var d, s;                     //Declare variables.  
   d = new Date();               //Create Date object.  
   d.setHours(nhr, nmin, nsec);  //Set hours, minutes, & seconds.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    //Return new date setting.  
}  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Относится к**: [Объект Date](../../javascript/reference/date-object-javascript.md)  
  
## См. также  
 [Метод getHours \(Date\)](../../javascript/reference/gethours-method-date-javascript.md)   
 [Метод getUTCHours \(Date\)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [Метод setUTCHours \(Date\)](../../javascript/reference/setutchours-method-date-javascript.md)