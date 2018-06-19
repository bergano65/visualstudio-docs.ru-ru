---
title: Метод setUTCMonth (Date) (JavaScript) | Документы Microsoft
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
- setUTCMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- setUTCMonth method
- Month method
- UTC dates, setting
ms.assetid: cdac5f64-c4fd-44cc-ba3a-9a8dd3dd3fad
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 02cb69026b66e3f307a8709ab3f5b23d9518643a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640954"
---
# <a name="setutcmonth-method-date-javascript"></a>Метод setUTCMonth (Date) (JavaScript)
Устанавливает значение месяца `Date` с помощью общего скоординированного времени (UTC).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.setUTCMonth(numMonth[, dateVal])   
```  
  
## <a name="parameters"></a>Параметры  
 `dateObj`  
 Обязательный. Любой объект `Date`.  
  
 `numMonth`  
 Обязательный. Числовое значение, представляющее месяц. Значение для января равно 0, а значения других месяцев увеличиваются.  
  
 `dateVal`  
 Необязательно. Числовое значение, представляющее день месяца. Если не задано, значением из вызова `getUTCDate` используется метод.  
  
## <a name="remarks"></a>Примечания  
 Чтобы установить значение месяца с помощью локального времени, используйте `setMonth` метод.  
  
 Если значение `numMonth` превышает 11 (январь соответствует месяцу 0), или является отрицательным числом, хранящееся значение года увеличивается или уменьшается соответствующим образом. Например, если сохранена дата «5 января 1996 00:00:00.00» и **setUTCMonth(14)** — вызывается, дата изменяется на «5 марта 1997 00:00:00.00».  
  
 **SetUTCFullYear** метод может использоваться для задания год, месяц и день месяца.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода `setUTCMonth`.  
  
```JavaScript  
function SetUTCMonthDemo(newmonth){  
   var d, s;                       // Declare variables.  
   d = new Date();                 // Create Date object.  
   d.setUTCMonth(newmonth);        // Set UTC month.  
   s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                      // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применимо к**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод getMonth (Date)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [Метод getUTCMonth (Date)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [Метод setMonth (Date)](../../javascript/reference/setmonth-method-date-javascript.md)