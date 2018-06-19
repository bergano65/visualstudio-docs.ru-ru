---
title: Метод setFullYear (Date) (JavaScript) | Документы Microsoft
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
- setFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Year method
- setFullYear method
- dates, setting
ms.assetid: 635e4f5a-0210-4c01-8152-b0da4146f6ff
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e5e20a8486d1aefeab9b244c5f1e9d1b1e60c3f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640354"
---
# <a name="setfullyear-method-date-javascript"></a>Метод setFullYear (Date) (JavaScript)
Задает год `Date` объекта с помощью локального времени.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.setFullYear(numYear[, numMonth[, numDate]])   
```  
  
## <a name="parameters"></a>Параметры  
 `dateObj`  
 Обязательный. Любой объект `Date`.  
  
 `numYear`  
 Обязательный. Числовое значение для года.  
  
 `numMonth`  
 Необязательно. Отсчитываемый от нуля числовое значение за месяц (0 для января, 11, за декабрь). Если необходимо указать `numDate` указано.  
  
 `numDate`  
 Необязательно. Числовое значение, представляющее день месяца.  
  
## <a name="remarks"></a>Примечания  
 Все **задать** методы, принимающие необязательные аргументы, используют значение, возвращенное из соответствующего **получить** методов, если аргумент не задан. Например если `numMonth` аргумент является необязательным, но не указано, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] использует значение, возвращенное из **getMonth** метод.  
  
 Кроме того Если значение аргумента больше, чем его календаря диапазона или является отрицательным, дата откатывается вперед или назад, соответствующим образом.  
  
 Чтобы установить год с помощью общего скоординированного времени (UTC), используйте `setUTCFullYear` метод.  
  
 Диапазон лет, поддерживаемых в объекте даты — приблизительно 285616 лет до и после 1970 года.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование `setFullYear` метода:  
  
```JavaScript  
var date1 = new Date("1/1/2001");  
date1.setFullYear(2007);  
  
var date2 = new Date("1/1/2001");  
date2.setFullYear(2008, 10, 3);   
  
document.write (date1.toLocaleString());  
document.write ("<br />");  
document.write (date2.toLocaleString());  
  
// Output:  
// Monday, January 01, 2007 12:00:00 AM  
// Monday, November 03, 2008 12:00:00 AM  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применимо к**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод getFullYear (Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [Метод getUTCFullYear (Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [Метод setUTCFullYear (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)