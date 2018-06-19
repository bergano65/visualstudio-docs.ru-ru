---
title: Свойство Format (Intl.DateTimeFormat) | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 487930fe-a948-446f-902d-06bb0d7685d5
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e94fcd797a63944d0162dceadf773cf9b15f943
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636594"
---
# <a name="format-property-intldatetimeformat"></a>Свойство format (Intl.DateTimeFormat)
Возвращает функцию, которая форматирует дату языкового стандарта с помощью параметров форматирования указанных даты и времени.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
dateTimeFormatObj.format  
```  
  
#### <a name="parameters"></a>Параметры  
 `dateTimeFormatObj`  
 Обязательный. Имя `DateTimeFormat` объект для использования в качестве модуля форматирования.  
  
## <a name="remarks"></a>Примечания  
 Функции, возвращенной методом `format` свойство принимает один аргумент, `date`и возвращает строку, представляющую локализованных дат, используя параметры, указанные в `DateTimeFormat` объекта. `date` Параметр возвращаемой функции должно быть число, Строка даты, или `Date` объекта. Если `date` не указан, функция использует [Date.now](../../javascript/reference/date-now-function-javascript.md) как входное значение по умолчанию.  
  
## <a name="example"></a>Пример  
 В следующем примере используется `DateTimeFormat` объект для локализации даты «1 декабря 2007 г.» на немецкий и отформатировать его.  
  
```JavaScript  
var dtFormat = new Intl.DateTimeFormat(["de"], {  
    year: "numeric",  
    month: "long",  
    day: "2-digit",  
    hour: "numeric"  
});  
  
if (console && console.log) {  
    console.log(dtFormat.format(new Date("Dec 1, 2007")));  
    // Returns 01. Dezember 2007 00:00  
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Объект Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)