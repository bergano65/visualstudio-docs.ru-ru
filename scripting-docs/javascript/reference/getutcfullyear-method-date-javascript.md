---
title: "Метод getUTCFullYear (Date) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getUTCFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- getUTCFullYear method
- Date object
- UTCFullYear method
- dates, UTC
- UTC dates, returning
- Full Year method
- UTC dates, getting
ms.assetid: f11e5363-ef8a-48dd-9d56-4ee7290c7c48
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c8268631a96eed1f61ef4ba908b78680c8522096
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="getutcfullyear-method-date-javascript"></a>Метод getUTCFullYear (Date) (JavaScript)
Возвращает год с помощью общего скоординированного времени (UTC).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.getUTCFullYear()   
```  
  
#### <a name="parameters"></a>Параметры  
 Обязательная ссылка `dateObj` — это объект `Date` .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает год в виде четырехзначного числа. Года, указанного двумя цифрами в `Date` конструктора или в `setFullYear` считаются в столетия, учитывая «5/14/12», поэтому `getUTCFullYear` возвращает «1912».  
  
## <a name="remarks"></a>Примечания  
 Чтобы получить год с помощью локального времени, используйте `getFullYear` метод.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать метод `getUTCFullYear`.  
  
```JavaScript  
var date = new Date("1/9/36");  
document.write(date.getUTCFullYear());  
  
// Output: 1936  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применимо к**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод getFullYear (Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [Метод setFullYear (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [Метод setUTCFullYear (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)