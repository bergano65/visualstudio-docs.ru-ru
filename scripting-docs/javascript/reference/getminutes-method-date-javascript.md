---
title: "Метод getMinutes (Date) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- GetMinutes method
- minutes method
ms.assetid: d4139b5d-04e1-474c-9a83-e9d40597243a
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff08fd84345c9ceb816444a1b44643a8353b60b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="getminutes-method-date-javascript"></a>Метод getMinutes (Date) (JavaScript)
Возвращает минуты `Date` объекта, с помощью локального времени.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.getMinutes()   
```  
  
#### <a name="parameters"></a>Параметры  
 Обязательная ссылка `dateObj` — это объект `Date` .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает целое число от 0 до 59. Возвращается значение 0, что время меньше одной минуты после часа. Если `Date` объект был создан без указания времени, по умолчанию значение равно 0.  
  
## <a name="remarks"></a>Примечания  
 Чтобы получить значение минут, с помощью общего скоординированного времени (UTC), используйте `getUTCMinutes` метод.  
  
## <a name="example"></a>Пример  
 В следующем примере показан способ `getMinutes` метод.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getMinutes());  
  
// Output:  
// 0  
// 5  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применимо к**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод getUTCMinutes (Date)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [Метод setMinutes (Date)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [Метод setUTCMinutes (Date)](../../javascript/reference/setutcminutes-method-date-javascript.md)