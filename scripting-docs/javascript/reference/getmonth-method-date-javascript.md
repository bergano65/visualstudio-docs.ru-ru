---
title: "Метод getMonth (Date) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, month value
- Month method
- GetMonth method
ms.assetid: c20dd8ba-1d78-42f1-8717-ed3dfd2362dd
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeffd7ffc7bee5fa63607e342a9a9dced7088d35
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="getmonth-method-date-javascript"></a>Метод getMonth (Date) (JavaScript)
Возвращает месяц, с помощью локального времени.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.getMonth()   
```  
  
#### <a name="parameters"></a>Параметры  
 Обязательная ссылка `dateObj` — это объект `Date` .  
  
## <a name="return-value"></a>Возвращаемое значение  
 `getMonth` Метод возвращает целое число от 0 (январь) до 11 (декабрь). Для `Date` создан с параметром «5 января 1996», `getMonth` возвращает 0.  
  
## <a name="remarks"></a>Примечания  
 Чтобы получить значение месяца, с помощью общего скоординированного времени (UTC), используйте `getUTCMonth` метод.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать метод `getMonth`.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getMonth());  
  
// Output: 0  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применимо к**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод getUTCMonth (Date)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [Метод setMonth (Date)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [Метод setUTCMonth (Date)](../../javascript/reference/setutcmonth-method-date-javascript.md)