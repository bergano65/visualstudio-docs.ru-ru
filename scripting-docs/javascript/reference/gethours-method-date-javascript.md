---
title: Метод getHours (Date) (JavaScript) | Документы Microsoft
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
- getHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- GetHours method
- Hours method
ms.assetid: c3936496-a213-4d15-b308-d53926ed310c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87170f96ee6ae6b4a825436717a94749cc336ee0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636624"
---
# <a name="gethours-method-date-javascript"></a>Метод getHours (Date) (JavaScript)
Возвращает часы в даты, с помощью локального времени.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.getHours()   
```  
  
#### <a name="parameters"></a>Параметры  
 Обязательная ссылка `dateObj` — это объект `Date` .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Целое число от 0 до 23, указывающее количество часов, истекших после полуночи. Если время, до 1:00:00, то возвращается ноль. Если `Date` объект был создан без указания времени, по умолчанию часа равно 0.  
  
## <a name="remarks"></a>Примечания  
 Чтобы получить значение часов, с помощью общего скоординированного времени (UTC), используйте `getUTCHours` метод.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать метод `getHours`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getHours());  
document.write("<br/>");  
  
date.setTime(50000000);  
document.write(date.getHours());  
  
// Output:  
// 0   
// 5  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применимо к**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод getUTCHours (Date)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [Метод setHours (Date)](../../javascript/reference/sethours-method-date-javascript.md)   
 [Метод setUTCHours (Date)](../../javascript/reference/setutchours-method-date-javascript.md)