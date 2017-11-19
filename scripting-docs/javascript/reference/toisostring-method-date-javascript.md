---
title: "Метод toISOString (Date) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toISOString method [JavaScript]
ms.assetid: 58577d8f-3ae8-4887-8687-26233ea79ff6
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 31559e1bc44849573ec7dc903411ce98b0a4440d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="toisostring-method-date-javascript"></a>Метод toISOString (Date) (JavaScript)
Возвращает дату в виде строкового значения в формате ISO.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
  
objDate.toISOString()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Строковое представление даты в международной организации стандартизации (ISO) формате.  
  
## <a name="exceptions"></a>Исключения  
 Если `objDate` не содержит допустимой датой `RangeError` исключения.  
  
## <a name="remarks"></a>Примечания  
 Формат ISO — это упрощение формата ISO 8601. Дополнительные сведения см. в разделе [строки даты и времени](../../javascript/date-and-time-strings-javascript.md).  
  
 Часовой пояс — всегда в формате UTC, обозначаемая суффиксом "Z" в выходных данных.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода `toISOString`.  
  
```JavaScript  
var dt = new Date("30 July 2010 15:05 UTC");  
document.write(dt.toISOString());  
document.write("<br />");  
document.write(dt.toUTCString());  
  
// Output:  
//  2010-07-30T15:05:00.000Z  
//  Fri, 30 Jul 2010 15:05:00 UTC  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Объект Date](../../javascript/reference/date-object-javascript.md)   
 [Строки даты и времени](../../javascript/date-and-time-strings-javascript.md)