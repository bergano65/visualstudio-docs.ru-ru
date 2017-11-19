---
title: "Метод getUTCSeconds (Date) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getUTCSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- UTC times, returning
- seconds method
- getUTCSeconds method
ms.assetid: 2d8ea7dc-79f8-4a9b-b2ab-732db2bcd5fd
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4f398145f8e31ed633bf3215de7d5a5ef669b7ef
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="getutcseconds-method-date-javascript"></a>Метод getUTCSeconds (Date) (JavaScript)
Возвращает секунды `Date` с помощью общего скоординированного времени (UTC).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.getUTCSeconds()   
```  
  
#### <a name="parameters"></a>Параметры  
 Обязательная ссылка `dateObj` — это объект `Date` .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает целое число от 0 до 59. Во время меньше одной секунды в текущей минуте, возвращается нуль. Если `Date` объект был создан без указания времени, по умолчанию времени в формате UTC, значение секунд равно 0.  
  
## <a name="remarks"></a>Примечания  
 Чтобы получить количество секунд в формате местного времени, используйте `getSeconds` метод.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать метод `getUTCSeconds`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date. getUTCSeconds());  
  
// Output: 0  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применимо к**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод getSeconds (Date)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [Метод setSeconds (Date)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [Метод setUTCSeconds (Date)](../../javascript/reference/setutcseconds-method-date-javascript.md)