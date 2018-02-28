---
title: "Метод getFullYear (Date) (JavaScript) | Документы Microsoft"
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
- getFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, returning year
- Date object
- getFullYear method
ms.assetid: f9ec1262-02e9-4791-90b5-48f33b1dc4bc
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 211d6c86435e39eb75b9b1ce3415738541ca07db
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="getfullyear-method-date-javascript"></a>Метод getFullYear (Date) (JavaScript)
Возвращает год, с помощью локального времени.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.getFullYear()   
```  
  
#### <a name="parameters"></a>Параметры  
 Обязательная ссылка `dateObj` — это объект `Date` .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Год в виде четырехзначного числа. Например 1976 год возвращается как 1976. Года, указанного двумя цифрами в `Date` конструктора или в `setFullYear` считаются в столетия, учитывая «5/14/12», поэтому `getFullYear` возвращает «1912».  
  
## <a name="remarks"></a>Примечания  
 Чтобы получить год с помощью общего скоординированного времени (UTC), используйте `getUTCFullYear` метод.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование **getFullYear** метод.  
  
```JavaScript  
var date = new Date("1/1/01");  
document.write(date.getFullYear());  
  
// Output: 1901  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применимо к**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод getUTCFullYear (Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [Метод setFullYear (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [Метод setUTCFullYear (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)