---
title: Функция Date.UTC (JavaScript) | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- UTC
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- UTC function [JavaScript]
- UTC dates, returning
- Date.UTC function [JavaScript]
ms.assetid: c0d67ce1-a47e-4dfd-bbf4-21619c406a0f
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a6a7c5622b74699e3d718ceb65e96638bdb6c3c5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636354"
---
# <a name="dateutc-function-javascript"></a>Функция Date.UTC (JavaScript)
Возвращает число миллисекунд, истекших с полуночи 1 января 1970 года общего скоординированного времени (UTC) (или среднего времени по Гринвичу) и указанной даты.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Date.UTC(year, month, day[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## <a name="parameters"></a>Параметры  
 `year`  
 Обязательный. Точность даты кросс-го века требуется полное указание года. Если `year` находится в диапазоне от 0 до 99 используется, затем `year` считается 1900 + `year`.  
  
 `month`  
 Обязательный. Месяц как целое число от 0 до 11 (Январь — Декабрь).  
  
 `day`  
 Обязательный. Дата как целое число от 1 до 31.  
  
 `hours`  
 Необязательно. Если необходимо указать `minutes` предоставляется. Целое число от 0 до 23 (от полуночи до 23: 00), представляющее час.  
  
 `minutes`  
 Необязательно. Если необходимо указать `seconds` предоставляется. Целое число от 0 до 59, представляющее минуты.  
  
 `seconds`  
 Необязательно. Если необходимо указать `milliseconds` предоставляется. Целое число от 0 до 59, представляющее секунды.  
  
 `ms`  
 Необязательно. Целое число от 0 до 999, представляющее миллисекунды.  
  
## <a name="remarks"></a>Примечания  
 `Date.UTC` Функция возвращает число миллисекунд, истекших с полуночи, 1 января 1970 г. UTC и заданной даты. Это возвращаемое значение может использоваться в `setTime` метод и в `Date` конструктор объекта. Если значение аргумента больше значения диапазона или является отрицательным числом, остальные хранящиеся значения изменяются соответствующим образом. Например, если задать 150 секунд [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] переопределит это число как две минуты и 30 секунд.  
  
 Разница между `Date.UTC` функции и `Date` является конструктором объекта даты, `Date.UTC` функции предполагается время в формате UTC и `Date` конструктор объекта предполагается локальное время.  
  
## <a name="example"></a>Пример  
 В следующем примере показано применение функции `Date.UTC`.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Метод setTime (Date)](../../javascript/reference/settime-method-date-javascript.md)