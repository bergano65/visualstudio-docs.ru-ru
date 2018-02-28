---
title: "Метод getTime (Date) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- getTime
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- GetTime method
- time method
ms.assetid: f0da1d4e-337c-497d-9205-093defbc6d3d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a31e542445e89a0e2f3364d36ae44f8d2d4cf9bb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="gettime-method-date-javascript"></a>Метод getTime (Date) (JavaScript)
Возвращает значение времени в миллисекундах.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.getTime()   
```  
  
#### <a name="parameters"></a>Параметры  
 Обязательная ссылка `dateObj` — это объект `Date` .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает число миллисекунд, истекших с полуночи 1 января 1970 года и значения времени в `Date` объекта. Диапазон дат — приблизительно 285616 лет в обе стороны от полуночи 1 января 1970 года. Отрицательные числа указывают даты до 1970 года.  
  
## <a name="remarks"></a>Примечания  
 При выполнении нескольких вычисления даты и времени, можно определить переменные, равное количество миллисекунд в дня, часа или минуты. Пример:  
  
```JavaScript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
```  
  
 В разделе [вычисления даты и времени (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md) Дополнительные сведения об использовании `getTime` метода.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать метод `getTime`.  
  
```JavaScript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
  
date = new Date("1/1/2001");  
var time = date.getTime();  
  
document.write(Math.round(time / day) + " days from 1/1/1970 to 1/1/2001");  
  
// Output: 11323 days from 1/1/1970 to 1/1/2001  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применимо к**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод setTime (Date)](../../javascript/reference/settime-method-date-javascript.md)