---
title: Метод setUTCMinutes (Date) (JavaScript) | Документы Microsoft
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
- setUTCMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- minutes
- dates, UTC
- UTC times, setting
- setUTCMinutes method
ms.assetid: 2415e788-6d28-46dd-a103-0931a1fd1446
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 37df1bcefa358f2c9076a3da877bd642d19178b0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640884"
---
# <a name="setutcminutes-method-date-javascript"></a>Метод setUTCMinutes (Date) (JavaScript)
Задает значение минут в `Date` с помощью общего скоординированного времени (UTC).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.setUTCMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## <a name="parameters"></a>Параметры  
 `dateObj`  
 Обязательный. Любой объект `Date`.  
  
 `numMinutes`  
 Обязательный. Числовое значение, равное значению минут. Должен быть указан при использовании любого из следующих аргументов.  
  
 *numSeconds*  
 Необязательно. Числовое значение, равное количеству секунд. Если необходимо указать `numMilli` используется.  
  
 `numMilli`  
 Необязательно. Числовое значение, равное количеству миллисекунд.  
  
## <a name="remarks"></a>Примечания  
 Все **задать** методы, принимающие необязательные аргументы, используют значение, возвращенное из соответствующего **получить** методов, если аргумент не задан. Например если *numSeconds* аргумент не указан, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] использует значение, возвращенное из `getUTCSeconds` метод.  
  
 Чтобы изменить значение минут с помощью локального времени, используйте `setMinutes` метод.  
  
 Если значение аргумента больше значения диапазона или является отрицательным числом, остальные хранящиеся значения изменяются соответствующим образом. Например, если сохранена дата «5 января 1996 00:00:00.00» и **setUTCMinutes(70)** — вызывается, дата изменяется на «5 января 1996 г.»  
  
 **SetUTCHours** метод может использоваться для задания часов, минут, секунд и миллисекунд.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование `setUTCMinutes` метода:  
  
```JavaScript  
function SetUTCMinutesDemo(nmin, nsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setUTCMinutes(nmin,nsec);  // Set UTC minutes.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                   // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применимо к**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод getMinutes (Date)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [Метод getUTCMinutes (Date)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [Метод setMinutes (Date)](../../javascript/reference/setminutes-method-date-javascript.md)