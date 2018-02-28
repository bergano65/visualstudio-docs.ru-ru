---
title: "Метод getUTCMilliseconds (Date) (JavaScript) | Документы Microsoft"
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
- getUTCMilliseconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- milliseconds
- UTC times, returning
- getUTCMilliseconds method
ms.assetid: 7491d387-7b6a-40df-89e5-55c64795ef70
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3fb7cf202c8511bec00c10dc5b8c23bd198d8700
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="getutcmilliseconds-method-date-javascript"></a>Метод getUTCMilliseconds (Date) (JavaScript)
Возвращает миллисекунды `Date` с помощью общего скоординированного времени (UTC).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.getUTCMilliseconds()   
```  
  
#### <a name="parameters"></a>Параметры  
 Обязательная ссылка `dateObj` — это объект `Date` .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение миллисекунд, которое может находиться в диапазоне от 0 до 999.  
  
## <a name="remarks"></a>Примечания  
 Чтобы получить количество миллисекунд в формате местного времени, используйте `getMilliseconds` метод.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода `getUTCMilliseconds`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMilliseconds());  
document.write("<br/>");  
  
date.setMilliseconds(34);  
document.writedate.getUTCMilliseconds());  
  
// Output:  
// 0   
// 34   
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применимо к**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод getMilliseconds (Date)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [Метод setMilliseconds (Date)](../../javascript/reference/setmilliseconds-method-date-javascript.md)   
 [Метод setUTCMilliseconds (Date)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)