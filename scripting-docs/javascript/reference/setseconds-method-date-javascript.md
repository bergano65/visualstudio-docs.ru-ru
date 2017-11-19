---
title: "Метод setSeconds (Date) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- setSeconds method
- seconds method
ms.assetid: 986ffa54-1db6-4af2-ab8b-8353f64f0b57
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b8d545307f6aac3506310c868a2860a6159a106
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="setseconds-method-date-javascript"></a>Метод setSeconds (Date) (JavaScript)
Задает значение секунд `Date` объекта с помощью локального времени.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj  
.setSeconds(  
numSeconds[, numMilli])   
```  
  
## <a name="parameters"></a>Параметры  
 `dateObj`  
 Обязательный. Любой объект `Date`.  
  
 *numSeconds*  
 Обязательный. Числовое значение, равное количеству секунд.  
  
 `numMilli`  
 Необязательно. Числовое значение, равное количеству миллисекунд.  
  
## <a name="remarks"></a>Примечания  
 Все **задать** методы, принимающие необязательные аргументы, используют значение, возвращенное из соответствующего **получить** методов, если аргумент не задан. Например если `numMilli` аргумент не указан, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] использует значение, возвращенное из **getMilliseconds** метод.  
  
 Чтобы установить значение, с помощью общего скоординированного времени (UTC) секунд, используйте `setUTCSeconds` метод.  
  
 Если значение аргумента больше значения диапазона или является отрицательным числом, остальные хранящиеся значения изменяются соответствующим образом. Например, если сохранена дата «5 января 1996 г. 00:00:00» и **метод setSeconds(150)** — вызове изменены для «5 января 1996 г. 00:02:30.»  
  
 `setHours` Метод может использоваться для задания часов, минут, секунд и миллисекунд.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода `setSeconds`.  
  
```JavaScript  
function SetSecondsDemo(nsec){  
   var d = new Date();         //Create Date object.  
   d.setSeconds(nsec);         //Set seconds.  
   var s = "Current setting is ";  
   s += d.toLocaleString();  
   return(s);                  //Return new setting.  
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применимо к**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод getSeconds (Date)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [Метод getUTCSeconds (Date)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [Метод setUTCSeconds (Date)](../../javascript/reference/setutcseconds-method-date-javascript.md)