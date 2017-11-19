---
title: "Метод setUTCHours (Date) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setUTCHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- UTC times, setting
- setUTCHours method
ms.assetid: 257e36fd-fb06-4a4d-8634-d66a020a1511
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9fe83735028f86d38ef270beac6c44dfa4caae7f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="setutchours-method-date-javascript"></a>Метод setUTCHours (Date) (JavaScript)
Задает значение часов в `Date` с помощью общего скоординированного времени (UTC).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.setUTCHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## <a name="parameters"></a>Параметры  
 `dateObj`  
 Обязательный. Любой объект `Date`.  
  
 `numHours`  
 Обязательный. Числовое значение, равное количеству часов.  
  
 `numMin`  
 Необязательно. Числовое значение, равное значению минут. Должен быть указан, если параметр `numSec` или `numMilli` используются.  
  
 `numSec`  
 Необязательно. Числовое значение, равное количеству секунд. Если необходимо указать `numMilli` используется аргумент.  
  
 `numMilli`  
 Необязательно. Числовое значение, равное количеству миллисекунд.  
  
## <a name="remarks"></a>Примечания  
 Все **задать** методы, принимающие необязательные аргументы, используют значение, возвращенное из соответствующего **получить** методов, если аргумент не задан. Например если `numMin` аргумент не указан, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] использует значение, возвращенное из `getUTCMinutes` метод.  
  
 Чтобы установить значение часов с помощью локального времени, используйте `setHours` метод.  
  
 Если значение аргумента больше значения диапазона или является отрицательным числом, остальные хранящиеся значения изменяются соответствующим образом. Например, если сохранена дата «5 января 1996 00:00:00.00» и **setUTCHours(30)** — вызывается, дата изменяется на «6 января 1996 г.»  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода `setUTCHours`.  
  
```JavaScript  
function SetUTCHoursDemo(nhr, nmin, nsec){     
   var d, s;                        // Declare variables.  
   d = new Date();                  // Create Date object.  
   d.setUTCHours(nhr, nmin, nsec);  // Set UTC hours, minutes, seconds.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                       // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применимо к**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод getHours (Date)](../../javascript/reference/gethours-method-date-javascript.md)   
 [Метод getUTCHours (Date)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [Метод setHours (Date)](../../javascript/reference/sethours-method-date-javascript.md)