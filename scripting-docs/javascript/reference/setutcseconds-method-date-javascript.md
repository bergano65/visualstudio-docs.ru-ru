---
title: "Метод setUTCSeconds (Date) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setUTCSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- setUTCSeconds method
- UTC times, setting
- seconds method
ms.assetid: e035e282-b39d-4d1d-8771-c17542fd6493
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f3df010cd84332d8957f1c08c41c4543dec36e4a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="setutcseconds-method-date-javascript"></a>Метод setUTCSeconds (Date) (JavaScript)
Задает значение секунд `Date` с помощью общего скоординированного времени (UTC).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.setUTCSeconds(numSeconds[, numMilli])   
```  
  
## <a name="parameters"></a>Параметры  
 `dateObj`  
 Обязательный. Любой объект `Date`.  
  
 *numSeconds*  
 Обязательный. Числовое значение, равное количеству секунд.  
  
 `numMilli`  
 Необязательно. Числовое значение, равное количеству миллисекунд.  
  
## <a name="remarks"></a>Примечания  
 Все **задать** методы, принимающие необязательные аргументы, используют значение, возвращенное из соответствующего **получить** методов, если аргумент не задан. Например если `numMilli` аргумент не указан, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] использует значение, возвращенное из `getUTCMilliseconds` метод.  
  
 Чтобы установить значение, с помощью локального времени секунд, используйте `setSeconds` метод.  
  
 Если значение аргумента больше значения диапазона или является отрицательным числом, остальные хранящиеся значения изменяются соответствующим образом. Например, если сохранена дата «5 января 1996 00:00:00.00» и **метод setSeconds(150)** — вызывается, дата изменяется на «5 января 1996 г.»  
  
 **SetUTCHours** метод может использоваться для задания часов, минут, секунд и миллисекунд.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода `setUTCSeconds`.  
  
```JavaScript  
function SetUTCSecondsDemo(nsec){  
// Create Date object.  
    var d = new Date();       
// Set UTC seconds.  
    d.setUTCSeconds(nsec);    
    var s = "Current setting is ";  
    s += d.toUTCString();  
// Return new setting.  
    return(s);                
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применимо к**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод getSeconds (Date)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [Метод getUTCSeconds (Date)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [Метод setSeconds (Date)](../../javascript/reference/setseconds-method-date-javascript.md)