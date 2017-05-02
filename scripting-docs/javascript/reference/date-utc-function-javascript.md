---
title: "Функция Date.UTC (JavaScript) | Microsoft Docs"
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
  - "UTC"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "UTC - функция [JavaScript]"
  - "даты в формате UTC, возврат"
  - "Date.UTC - функция [JavaScript]"
ms.assetid: c0d67ce1-a47e-4dfd-bbf4-21619c406a0f
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Функция Date.UTC (JavaScript)
Возвращает количество миллисекунд, истекших с полуночи 1 января 1970 года по времени в формате UTC \(или GMT\) до заданной даты.  
  
## Синтаксис  
  
```  
Date.UTC(year, month, day[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## Параметры  
 `year`  
 Обязательный.  Чтобы обеспечить точность даты в разных веках, необходимо полное указание года.  Если используется значение `year` в диапазоне от 0 до 99, то предполагается, что `year` соответствует значению 1900 \+ `year`.  
  
 `month`  
 Обязательный.  Месяц в виде целого числа от 0 до 11 \(с января по декабрь\).  
  
 `day`  
 Обязательный.  Дата в виде целого числа в диапазоне от 1 до 31.  
  
 `hours`  
 Необязательный.  Должно быть указано, если указано значение `minutes`.  Целое число от 0 до 23 \(от полуночи до 23:00\), представляющее час.  
  
 `minutes`  
 Необязательный.  Должно быть указано, если указано значение `seconds`.  Целое число от 0 до 59, представляющее минуты.  
  
 `seconds`  
 Необязательный.  Должно быть указано, если указано значение `milliseconds`.  Целое число от 0 до 59, представляющее секунды.  
  
 `ms`  
 Необязательный.  Целое число от 0 до 999, представляющее миллисекунды.  
  
## Заметки  
 Функция `Date.UTC` возвращает количество миллисекунд, истекших с полуночи 1 января 1970 года по времени UTC до указанной даты.  Это возвращаемое значение может использоваться методом `setTime` и конструктором объекта `Date`.  Если значение аргумента превышает верхнюю границу его диапазона или является отрицательным числом, остальные хранящиеся значения изменяются соответственно.  Например, если задать 150 секунд, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] переопределит это число как две минуты и 30 секунд.  
  
 Различие между функцией `Date.UTC` и конструктором объекта `Date` состоит в том, что в функции `Date.UTC` предполагается время UTC, а в конструкторе объекта `Date` предполагается местное время.  
  
## Пример  
 В следующем примере показано использование функции `Date.UTC`.  
  
```javascript  
// Determine the milliseconds per day.  
 var MinMilli = 1000 * 60;  
var HrMilli = MinMilli * 60;  
var DyMilli = HrMilli * 24;  
  
var date = new Date("June 1, 1990");  
var year = date.getFullYear();  
var month = date.getMonth();  
var day = date.getDay();  
  
var newDay = new Date("January 16, 2020");  
var yeartoday = newDay.getUTCFullYear();  
var monthtoday = newDay.getUTCMonth();  
var dayofmonthtoday = newDay.getUTCDate();  
  
// Get the milliseconds since 1/1/1970 UTC.  
var t1 = Date.UTC(year, month - 1, day)  
var t2 = Date.UTC(yeartoday, monthtoday, dayofmonthtoday);  
  
// Determine the difference in days.  
var days = (t2 - t1) / DyMilli;  
  
document.write(days);  
// Output: 10848  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Метод setTime \(Date\)](../../javascript/reference/settime-method-date-javascript.md)