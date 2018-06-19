---
title: Метод toUTCString (Date) (JavaScript) | Документы Microsoft
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
- toUTCString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- UTC dates, converting to strings
- toUTCString method
ms.assetid: eb0983ed-7884-42fa-a2cc-de92b3111207
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bd5efc43152c1af2dd467b73dce235e8fe52f29
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640744"
---
# <a name="toutcstring-method-date-javascript"></a>Метод toUTCString (Date) (JavaScript)
Возвращает дату, преобразованную в строку с помощью общего скоординированного времени (UTC).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.toUTCString()   
```  
  
## <a name="remarks"></a>Примечания  
 Необходимая `dateObj` ссылка представляет собой любой `Date` объекта.  
  
 `toUTCString` Возвращает метод `String` , содержащий дату в формате UTC соглашение в удобном, легко чтение формы.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода `toUTCString`.  
  
```JavaScript  
function toUTCStrDemo(){  
   var d, s;                   //Declare variables.  
   d = new Date();             //Create Date object.  
   s = "Current setting is ";  
   s += d.toUTCString();       //Convert to UTC string.  
   return(s);                  //Return UTC string.  
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применимо к**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод toGMTString (Date)](../../javascript/reference/togmtstring-method-date-javascript.md)