---
title: "Метод setTime (Date) (JavaScript) | Документы Microsoft"
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
- setTime
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- SetTime method
- time method
ms.assetid: 86584748-7219-495b-bf56-e27f5782778c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e66b1fbf5d668330eb727e8bfc50ee9d11a28be3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="settime-method-date-javascript"></a>Метод setTime (Date) (JavaScript)
Задает значение даты и времени в `Date` объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.setTime(milliseconds)   
```  
  
## <a name="parameters"></a>Параметры  
 `dateObj`  
 Обязательный. Любой объект `Date`.  
  
 *миллисекунд*  
 Обязательный. Числовое значение, представляющее количество миллисекунд, прошедших с полуночи 1 января 1970 г. GMT.  
  
## <a name="remarks"></a>Примечания  
 Если *миллисекунд* имеет отрицательное значение, он указывает даты до 1970 года. Диапазон доступных дат — приблизительно 285616 лет 1970 года.  
  
 При установке даты и времени с `setTime` метод не зависит от часового пояса.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода `setTime`.  
  
```JavaScript  
function SetTimeTest(newtime){  
   var d, s;                  //Declare variables.  
   d = new Date();            //Create Date object.  
   d.setTime(newtime);        //Set time.  
   s = "Current setting is ";  
   s += d.toUTCString();  
   return(s);                 //Return new setting.  
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применимо к**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод getTime (Date)](../../javascript/reference/gettime-method-date-javascript.md)