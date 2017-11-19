---
title: "Метод setUTCDate (Date) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setUTCDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- dates, setting
- UTC dates, setting
- setUTCDate method
ms.assetid: e6c3b876-70fe-4103-b197-6c84c078ce10
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5631a36c8b1c4f1ee50dcadb39f0f21ae5aa28e3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="setutcdate-method-date-javascript"></a>Метод setUTCDate (Date) (JavaScript)
Задает числовое значение дня месяца в `Date` с помощью общего скоординированного времени (UTC).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.setUTCDate(numDate)   
```  
  
## <a name="parameters"></a>Параметры  
 `dateObj`  
 Обязательный. Любой объект `Date`.  
  
 *numDate*  
 Обязательный. Числовое значение, обозначающее день месяца.  
  
## <a name="remarks"></a>Примечания  
 Чтобы задать число месяца, с помощью локального времени, используйте `setDate` метод.  
  
 Если значение *numDate* больше, чем число дней в месяце, сохраненном в **даты** объекта или является отрицательным числом, дата имеет значение даты, равное *numDate* минус число дней в сохраненном месяце. Например, если сохранена дата — 5 января 1996 г. и **setUTCDate(32)** вызывается изменения даты на 1 февраля 1996 г. Отрицательные числа ведут себя одинаково.  
  
 **SetUTCFullYear** метод может использоваться для задания год, месяц и день месяца.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода `setUTCDate`.  
  
```JavaScript  
function SetUTCDateDemo(newdayofmonth){  
   var d = new Date();           // Create Date object.  
   d.setUTCDate(newdayofmonth);  // Set UTC day of month.  
   var s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                    // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применимо к**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод getDate (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Метод getUTCDate (Date)](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [Метод setDate (Date)](../../javascript/reference/setdate-method-date-javascript.md)