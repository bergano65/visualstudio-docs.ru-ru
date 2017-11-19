---
title: "Метод setHours (Date) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- hours
- setHours method
- dates, setting
ms.assetid: 460f742d-f8d2-4874-9d07-2fb969fef066
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f9757f8416953eaf756dba96b91100527606cf9c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="sethours-method-date-javascript"></a>Метод setHours (Date) (JavaScript)
Задает значение часов `Date` объекта с помощью локального времени.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.setHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## <a name="parameters"></a>Параметры  
 `dateObj`  
 Обязательный. Любой объект `Date`.  
  
 `numHours`  
 Обязательный. Числовое значение, равное количеству часов.  
  
 `numMin`  
 Необязательно. Числовое значение, равное значению минут. Должен быть указан при использовании любого из следующих аргументов.  
  
 `numSec`  
 Необязательно. Числовое значение, равное количеству секунд. Необходимо указать, если используется следующий аргумент.  
  
 `numMilli`  
 Необязательно. Числовое значение, равное количеству миллисекунд.  
  
## <a name="remarks"></a>Примечания  
 Все **задать** методы, принимающие необязательные аргументы, используют значение, возвращенное из соответствующего **получить** методов, если аргумент не задан. Например если `numMinutes` аргумент не указан, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] использует значение, возвращенное из `getMinutes` метод.  
  
 Чтобы установить значение часов, с помощью общего скоординированного времени (UTC), используйте `setUTCHours` метод.  
  
 Если значение аргумента больше значения диапазона или является отрицательным числом, остальные хранящиеся значения изменяются соответствующим образом. Например, если сохранена дата «5 января 1996 г. 00:00:00», и **метод setHours(30)** — вызове изменены для «6 января 1996 г. 06:00:00.» Отрицательные числа ведут себя одинаково.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода `setHours`.  
  
```JavaScript  
function SetHoursDemo(nhr, nmin, nsec){  
   var d, s;                     //Declare variables.  
   d = new Date();               //Create Date object.  
   d.setHours(nhr, nmin, nsec);  //Set hours, minutes, & seconds.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    //Return new date setting.  
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применимо к**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод getHours (Date)](../../javascript/reference/gethours-method-date-javascript.md)   
 [Метод getUTCHours (Date)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [Метод setUTCHours (Date)](../../javascript/reference/setutchours-method-date-javascript.md)