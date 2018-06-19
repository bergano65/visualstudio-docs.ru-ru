---
title: Метод setMonth (Date) (JavaScript) | Документы Microsoft
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
- setMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Month method
- setMonth method
ms.assetid: 4f5be295-d536-46c0-b3a4-ad06457efe82
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f2672abebd327af8b0da58d46ebc183b8159711
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640264"
---
# <a name="setmonth-method-date-javascript"></a>Метод setMonth (Date) (JavaScript)
Устанавливает значение месяца `Date` объекта с помощью локального времени.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj. setMonth(numMonth[, dateVal])   
```  
  
## <a name="parameters"></a>Параметры  
 `dateObj`  
 Обязательный. Любой объект `Date`.  
  
 `numMonth`  
 Обязательный. Числовое значение, представляющее месяц. Значение для января равно 0, а значения других месяцев увеличиваются.  
  
 `dateVal`  
 Необязательно. Числовое значение, представляющее день месяца. Если это значение не задано, значением из вызова `getDate` используется метод.  
  
## <a name="remarks"></a>Примечания  
 Чтобы установить значение месяца, с помощью общего скоординированного времени (UTC), используйте `setUTCMonth` метод.  
  
 Если значение `numMonth` превышает 11 (январь соответствует месяцу 0) или является отрицательным числом, хранящееся значение года изменяется соответствующим образом. Например, если сохранена дата «5 января 1996 г.» и **setMonth(14)** является именем, дата изменяется на «5 марта 1997.»  
  
 **SetFullYear** метод может использоваться для задания год, месяц и день месяца.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода `setMonth`.  
  
```JavaScript  
date = new Date('1/1/1990');  
date.setMonth(14);  
document.write(date);  
  
// Output: Fri Mar 1 00:00:00 PST 1991  
// Note that the time zone corresponds to the time zone on the local computer.  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применимо к**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод getMonth (Date)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [Метод getUTCMonth (Date)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [Метод setUTCMonth (Date)](../../javascript/reference/setutcmonth-method-date-javascript.md)