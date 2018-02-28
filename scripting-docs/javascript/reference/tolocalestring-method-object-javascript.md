---
title: "Метод toLocaleString (Object) (JavaScript) | Документы Microsoft"
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
- toLocaleString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toLocaleString method
ms.assetid: 0901afcb-126b-4ed7-bd6a-2301d50e2326
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f88e1c702cd8a7d702630ae90ef840c4af88f30
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="tolocalestring-method-object-javascript"></a>Метод toLocaleString (Object) (JavaScript)
Возвращает дату, преобразуется в строку, используя текущий языковой стандарт.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.toLocaleString()   
```  
  
## <a name="remarks"></a>Примечания  
 Необходимая `dateObj` любой `Date` объекта.  
  
 `toLocaleString` Возвращает метод `String` , содержащий дату, записанную в длинный формат текущего языкового стандарта.  
  
-   Для дат между 1601 и 1999 г. нашей эры даты форматируется в соответствии с региональные параметры пользователя элемента управления панели.  
  
-   Для дат за пределами этого диапазона, по умолчанию формат **toString** используется метод.  
  
 Например, в Соединенных Штатах `toLocaleString` возвращает «01/05/96 00:00:00» для 5 января. В Европе, он возвращает «01/05/96 00:00:00» для той же даты как европейскому помещает за предыдущий день месяца.  
  
> [!NOTE]
>  `toLocaleString`можно использовать только для отображения результатов для пользователя. он должен нельзя использовать в качестве основы для вычислений в сценарии как возвращаемый результат зависит от конкретного компьютера.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода `toLocaleString`.  
  
```JavaScript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применяется к**: [объект Array](../../javascript/reference/array-object-javascript.md)&#124; [Дата объекта](../../javascript/reference/date-object-javascript.md)&#124; [Номер объекта](../../javascript/reference/number-object-javascript.md)&#124; [Объекта](../../javascript/reference/object-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод toLocaleDateString (Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)