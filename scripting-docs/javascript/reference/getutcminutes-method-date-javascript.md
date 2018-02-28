---
title: "Метод getUTCMinutes (Date) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- getUTCMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- minutes
- UTC times, returning
- getUTCMinutes method
ms.assetid: b6d92543-b285-4e46-8f47-bba36e53fabd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe691d3b52d18340eeeff81a91c049a262277c54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="getutcminutes-method-date-javascript"></a>Метод getUTCMinutes (Date) (JavaScript)
Возвращает минуты `Date` с помощью общего скоординированного времени (UTC).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.getUTCMinutes()   
```  
  
#### <a name="parameters"></a>Параметры  
 Обязательная ссылка `dateObj` — это объект `Date` .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает целое число от 0 до 59. Возвращается значение 0, что время меньше одной минуты после часа. Если `Date` объект был создан без указания времени, по умолчанию времени в формате UTC значение 0. Однако в других часовых поясах он может быть разным.  
  
## <a name="remarks"></a>Примечания  
 Чтобы получить количество минут, сохраненных с помощью локального времени, используйте `getMinutes` метод.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода `getUTCMinutes`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getUTCMinutes());  
  
// Output:   
// 0  
// 5  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применимо к**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод getMinutes (Date)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [Метод setMinutes (Date)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [Метод setUTCMinutes (Date)](../../javascript/reference/setutcminutes-method-date-javascript.md)