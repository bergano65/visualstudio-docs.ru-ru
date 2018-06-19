---
title: Метод setMilliseconds (Date) (JavaScript) | Документы Microsoft
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
- setMilliseconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- milliseconds
- setMilliseconds method
ms.assetid: 6c398961-130e-4f60-802f-6c30e1ef4de4
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0cd339e1352511312ef9a9abf9a7ff02955c986
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639804"
---
# <a name="setmilliseconds-method-date-javascript"></a>Метод setMilliseconds (Date) (JavaScript)
Устанавливает значение миллисекунд `Date` объекта с помощью локального времени.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.  
setMilliseconds(  
numMilli  
)   
```  
  
## <a name="parameters"></a>Параметры  
 `dateObj`  
 Обязательный. Любой объект `Date`.  
  
 `numMilli`  
 Обязательный. Числовое значение, равное количеству миллисекунд.  
  
## <a name="remarks"></a>Примечания  
 Чтобы установить значение миллисекунд с помощью общего скоординированного времени (UTC), используйте `setUTCMilliseconds` метод.  
  
 Если значение `numMilli` превышает 999 или является отрицательным числом, увеличивается число секунд (минуты, часы и так далее, при необходимости) требуемого.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода `setMilliseconds`.  
  
```JavaScript  
function SetMSecDemo(nmsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setMilliseconds(nmsec);    // Set milliseconds.  
   s = "Current setting is ";  
   s += d.toLocaleString();  
   s += " and " + d.getMilliseconds();  
   s += " milliseconds";  
   return(s);                   // Return new date setting.  
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применимо к**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод getMilliseconds (Date)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [Метод getUTCMilliseconds (Date)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [Метод setUTCMilliseconds (Date)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)