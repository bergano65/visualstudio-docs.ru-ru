---
title: "Метод setMinutes (Date) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- minutes
- setMinutes method
ms.assetid: 34c959cd-cd29-4cee-8e04-9061cf6d42f3
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ce40cb3ebf769cdd8f668e246e272833780434d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="setminutes-method-date-javascript"></a>Метод setMinutes (Date) (JavaScript)
Задает значение минут в **даты** объекта с помощью локального времени.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.setMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## <a name="parameters"></a>Параметры  
 `dateObj`  
 Обязательный. Любой объект `Date`.  
  
 `numMinutes`  
 Обязательный. Числовое значение, равное значению минут. Должен быть указан при использовании любого из следующих аргументов.  
  
 *numSeconds*  
 Необязательно. Числовое значение, равное количеству секунд. Если необходимо указать `numMilli` используется аргумент.  
  
 `numMilli`  
 Необязательно. Числовое значение, равное количеству миллисекунд.  
  
## <a name="remarks"></a>Примечания  
 Все **задать** методы, принимающие необязательные аргументы, используют значение, возвращенное из соответствующего **получить** методов, если аргумент не задан. Например если *numSeconds* не указан аргумент [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] использует значение, возвращенное из `getSeconds` метод.  
  
 Чтобы задать значение минут, с помощью общего скоординированного времени (UTC), используйте `setUTCMinutes` метод.  
  
 Если значение аргумента больше значения диапазона или является отрицательным числом, остальные хранящиеся значения изменяются соответствующим образом. Например, если сохранена дата «5 января 1996 г. 00:00:00» и **метод setMinutes(90)** — вызове изменены для «5 января 1996 г. 01:30:00.» Отрицательные числа ведут себя одинаково.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода `setMinutes`.  
  
```JavaScript  
function SetMinutesDemo(nmin, nsec){  
   var d, s;                     // Declare variables.  
   d = new Date();               // Create Date object.  
   d.setMinutes(nmin, nsec);     // Set minutes.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применимо к**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод getMinutes (Date)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [Метод getUTCMinutes (Date)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [Метод setUTCMinutes (Date)](../../javascript/reference/setutcminutes-method-date-javascript.md)