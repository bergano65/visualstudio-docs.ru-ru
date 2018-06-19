---
title: Метод getSeconds (Date) (JavaScript) | Документы Microsoft
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
- getSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- seconds method
- GetSeconds method
ms.assetid: 97b10674-af0b-4681-a846-38f972196501
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 151d720b92fb9d7068c320983a25b965078f1b2e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636784"
---
# <a name="getseconds-method-date-javascript"></a>Метод getSeconds (Date) (JavaScript)
Возвращает секунды `Date` объекта, с помощью локального времени.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.getSeconds()   
```  
  
#### <a name="parameters"></a>Параметры  
 Обязательная ссылка `dateObj` — это объект `Date` .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает целое число от 0 до 59. Во время меньше одной секунды в текущей минуте, возвращается нуль. Если `Date` объект был создан без указания времени, по умолчанию значение секунд равно 0.  
  
## <a name="remarks"></a>Примечания  
 Чтобы получить секунды значения с помощью общего скоординированного времени (UTC), используйте `getUTCSeconds` метод.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать метод `getSeconds`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getSeconds());  
document.write("<br/>");  
  
date.setSeconds(5);  
document.write(date.getSeconds());  
  
// Output:  
// 0  
// 5  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применимо к**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод getUTCSeconds (Date)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [Метод setSeconds (Date)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [Метод setUTCSeconds (Date)](../../javascript/reference/setutcseconds-method-date-javascript.md)