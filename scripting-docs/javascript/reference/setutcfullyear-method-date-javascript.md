---
title: Метод setUTCFullYear (Date) (JavaScript) | Документы Microsoft
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
- setUTCFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- setUTCFullYear method
- UTC dates, setting
ms.assetid: e6c51b49-0149-4f9a-aa74-c73c0306f98e
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dda8b75dd8bc8dac87ea383546f392b064c1d63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640994"
---
# <a name="setutcfullyear-method-date-javascript"></a>Метод setUTCFullYear (Date) (JavaScript)
Устанавливает значение года `Date` с помощью общего скоординированного времени (UTC).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.setUTCFullYear(numYear[, numMonth[, numDate]])   
```  
  
## <a name="parameters"></a>Параметры  
 `dateObj`  
 Обязательный. Любой объект `Date`.  
  
 `numYear`  
 Обязательный. Числовое значение, представляющее год.  
  
 `numMonth`  
 Необязательно. Числовое значение, представляющее месяц. Значение для января равно 0, а значения других месяцев увеличиваются. Если необходимо указать *numDate* предоставляется.  
  
 *numDate*  
 Необязательно. Числовое значение, обозначающее день месяца.  
  
## <a name="remarks"></a>Примечания  
 Все **задать** методы, принимающие необязательные аргументы, используют значение, возвращенное из соответствующего **получить** методов, если аргумент не задан. Например если `numMonth` аргумент не указан, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] использует значение, возвращенное из `getUTCMonth` метод.  
  
 Кроме того, если значение аргумента больше, диапазона или является отрицательным числом, остальные хранящиеся значения изменяются соответствующим образом.  
  
 Чтобы установить год с помощью локального времени, используйте `setFullYear` метод.  
  
 Диапазон лет, поддерживаемых в `Date` объекта составляет приблизительно 285616 лет в каждую сторону от 1970 года.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода `setUTCFullYear`.  
  
```JavaScript  
var dtFirst = new Date();  
dtFirst.setUTCFullYear(2007);  
  
var dtSecond = new Date();  
// 10 is the value for November.   
dtSecond.setUTCFullYear(2008, 10, 3);   
  
document.write (dtFirst.toUTCString());  
document.write ("<br />");  
document.write (dtSecond.toUTCString());  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применимо к**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод getFullYear (Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [Метод getUTCFullYear (Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [Метод setFullYear (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)