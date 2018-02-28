---
title: "Функция Date.Parse (JavaScript) | Документы Microsoft"
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
- parse
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- parse function [JavaScript]
- Date.parse function [JavaScript]
ms.assetid: ed737e50-6398-4462-8779-2af3c03f8325
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a73fda66ef24df17a5213a182c04667fc4dfabf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="dateparse-function-javascript"></a>Функция Date.parse (JavaScript)
Анализирует строку, содержащую дату и возвращает количество миллисекунд, истекших с полуночи 1 января 1970 года.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Date.parse(dateVal)   
```  
  
## <a name="remarks"></a>Примечания  
 Необходимая `dateVal` аргумент является строка, содержащая дату или значение VT_DATE, извлеченное из объекта ActiveX или другого объекта. Для строк сведений о дате, `Date.parse` функции можно провести синтаксический анализ. в разделе [строки даты и времени](../../javascript/date-and-time-strings-javascript.md).  
  
 `Date.parse` Функция возвращает целое число, представляющее количество миллисекунд, истекших с полуночи 1 января 1970 года до даты, указанной в `dateVal`.  
  
## <a name="example"></a>Пример  
 В следующем примере показано применение функции `Date.parse`.  
  
```JavaScript  
var dateString = "November 1, 1997 10:15 AM";  
var mSec = Date.parse(dateString);  
document.write(mSec);  
// Output: 878404500000  
```  
  
## <a name="example"></a>Пример  
 Следующий пример возвращает разницу между указанной датой и 1/1 января 1970 года.  
  
```JavaScript  
var minMilli = 1000 * 60;  
var hrMilli = minMilli * 60;  
var dyMilli = hrMilli * 24;  
  
var testDate = new Date("June 1, 1990");  
var ms = Date.parse(testDate);  
var days = Math.round(ms / dyMilli);  
  
var dateStr = "";  
dateStr += "There are " + days + " days ";  
dateStr += "between 01/01/1970 and " + testDate;  
document.write(dateStr);  
  
// Output: There are 7456 days between 01/01/1970 and Fri Jun 1 00:00:00 PDT 1990  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Метод getDate (Date)](../../javascript/reference/getdate-method-date-javascript.md)