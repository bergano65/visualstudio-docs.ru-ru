---
title: "Дата объект (JavaScript) | Документы Microsoft"
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
- Date
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, determining
ms.assetid: ce2202bb-7ec9-4f5a-bf48-3a04feff283e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb5d53f3bddfeb3a3ed1ab36e2b4be822964eba5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="date-object-javascript"></a>Объект Date (JavaScript)
Обеспечивает базовые функции сохранения и получения данных даты и времени.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      dateObj = new Date()  
dateObj = new Date(dateVal)  
dateObj = new Date(year, month, date[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## <a name="parameters"></a>Параметры  
 `dateObj`  
 Обязательный. Имя переменной, которой присваивается объект `Date`.  
  
 `dateVal`  
 Обязательный. Если числовое значение `dateVal` представляет количество миллисекунд в формате UTC между указанной датой и полуночи 1 января 1970 года. Если строка, `dateVal` анализируется в соответствии с правилами в [строки даты и времени](../../javascript/date-and-time-strings-javascript.md). `dateVal` Аргумент также может иметь значение VT_DATE, возвращенный в результате некоторые объекты ActiveX.  
  
 `year`  
 Обязательный. Полный год, например, 1976 (а не 76).  
  
 `month`  
 Обязательный. Месяц как целое число от 0 до 11 (Январь — Декабрь).  
  
 `date`  
 Обязательный. Дата как целое число от 1 до 31.  
  
 `hours`  
 Необязательно. Если необходимо указать `minutes` предоставляется. Целое число от 0 до 23 (от полуночи до 23: 00), представляющее час.  
  
 минуты  
 Необязательно. Если необходимо указать `seconds` предоставляется. Целое число от 0 до 59, представляющее минуты.  
  
 `seconds`  
 Необязательно. Если необходимо указать `milliseconds` предоставляется. Целое число от 0 до 59, представляющее секунды.  
  
 `ms`  
 Необязательно. Целое число от 0 до 999, представляющее миллисекунды.  
  
## <a name="remarks"></a>Примечания  
 Объект `Date` объект содержит число, представляющее конкретный момент времени с точностью до миллисекунд. Если значение аргумента больше значения диапазона или является отрицательным числом, остальные хранящиеся значения изменяются соответствующим образом. Например, если задать 150 секунд [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] переопределит это число как две минуты и 30 секунд.  
  
 Если число `NaN`, объект не представляет конкретного момента времени. Если параметры не передаются `Date` объекта, он инициализируется в текущий момент времени (UTC). Значение должно быть задано для объекта, прежде чем использовать его.  
  
 Диапазон дат, которые могут быть представлены в `Date` объекта составляет приблизительно 285616 лет с обеих сторон от 1 января 1970 года.  
  
 В разделе [вычисления даты и времени (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md) Дополнительные сведения об использовании `Date` и связанные методы объекта.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование объекта `Date`.  
  
```JavaScript  
var dateString = "Today's date is: ";  
  
var newDate = new Date();  
  
// Get the month, day, and year.  
dateString += (newDate.getMonth() + 1) + "/";  
dateString += newDate.getDate() + "/";  
dateString += newDate.getFullYear();  
  
document.write(dateString);  
  
// Output: Today's date is: <date>  
```  
  
## <a name="requirements"></a>Требования  
 `Date object` появился в [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)]. Некоторые члены в следующих списках были введены в более поздних версиях. Дополнительные сведения см. в разделе [сведения о версии](../../javascript/reference/javascript-version-information.md) или документации для отдельных членов.  
  
## <a name="properties"></a>Свойства  
 В следующей таблице перечислены свойства объекта `Date Object`.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|[Свойство constructor](../../javascript/reference/constructor-property-date.md)|Указывает функцию, которая создает объект.|  
|[Свойство prototype](../../javascript/reference/prototype-property-date.md)|Возвращает ссылку на прототип класса объектов.|  
  
## <a name="functions"></a>Функции  
 В следующей таблице перечислены функции объекта `Date Object`.  
  
|Функции|Описание|  
|---------------|-----------------|  
|[Функция Date.now](../../javascript/reference/date-now-function-javascript.md)|Возвращает число миллисекунд, истекших с 1 января 1970 года, текущую дату и время.|  
|[Функция Date.parse](../../javascript/reference/date-parse-function-javascript.md)|Анализирует строку, содержащую дату и возвращает количество миллисекунд, истекших с полуночи 1 января 1970 года.|  
|[Функция Date.UTC](../../javascript/reference/date-utc-function-javascript.md)|Возвращает число миллисекунд, истекших с полуночи 1 января 1970 года общего скоординированного времени (UTC) (или среднего времени по Гринвичу) до указанной даты.|  
  
<a name="js56jsobjdatemeth"></a>   
## <a name="methods"></a>Методы  
 В следующей таблице перечислены методы объекта `Date Object`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Метод getDate](../../javascript/reference/getdate-method-date-javascript.md)|Возвращает значение дня месяца, с помощью локального времени.|  
|[Метод getDay](../../javascript/reference/getday-method-date-javascript.md)|Возвращает значение дня недели, с помощью локального времени.|  
|[Метод getFullYear](../../javascript/reference/getfullyear-method-date-javascript.md)|Возвращает значение года, с помощью локального времени.|  
|[Метод getHours](../../javascript/reference/gethours-method-date-javascript.md)|Возвращает значение часов с помощью локального времени.|  
|[Метод getMilliseconds](../../javascript/reference/getmilliseconds-method-date-javascript.md)|Возвращает значение миллисекунд с помощью локального времени.|  
|[Метод getMinutes](../../javascript/reference/getminutes-method-date-javascript.md)|Возвращает значение минут с помощью локального времени.|  
|[Метод getMonth](../../javascript/reference/getmonth-method-date-javascript.md)|Возвращает значение месяца с помощью локального времени.|  
|[Метод getSeconds](../../javascript/reference/getseconds-method-date-javascript.md)|Возвращает значение секунд с помощью локального времени.|  
|[Метод getTime](../../javascript/reference/gettime-method-date-javascript.md)|Возвращает значение времени в `Date` объект как количество миллисекунд, прошедших с полуночи 1 января 1970 года.|  
|[Метод getTimezoneOffset](../../javascript/reference/gettimezoneoffset-method-date-javascript.md)|Возвращает разницу в минутах между временем на главном компьютере и общего скоординированного времени (UTC).|  
|[Метод getUTCDate](../../javascript/reference/getutcdate-method-date-javascript.md)|Возвращает значение день месяца, в формате UTC.|  
|[Метод getUTCDay](../../javascript/reference/getutcday-method-date-javascript.md)|Возвращает значение дня недели, в формате UTC.|  
|[Метод getUTCFullYear](../../javascript/reference/getutcfullyear-method-date-javascript.md)|Возвращает значение года, в формате UTC.|  
|[Метод getUTCHours](../../javascript/reference/getutchours-method-date-javascript.md)|Возвращает значение часов, в формате UTC.|  
|[Метод getUTCMilliseconds](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)|Возвращает значение миллисекунд, в формате UTC.|  
|[Метод getUTCMinutes](../../javascript/reference/getutcminutes-method-date-javascript.md)|Возвращает значение минут, в формате UTC.|  
|[Метод getUTCMonth](../../javascript/reference/getutcmonth-method-date-javascript.md)|Возвращает значение месяца, в формате UTC.|  
|[Метод getUTCSeconds](../../javascript/reference/getutcseconds-method-date-javascript.md)|Возвращает значение, в формате UTC секунд.|  
|[Метод getVarDate](../../javascript/reference/getvardate-method-date-javascript.md)|Возвращает значение VT_DATE в `Date` объекта.|  
|[Метод getYear](../../javascript/reference/getyear-method-date-javascript.md)|Возвращает значение года.|  
|[Метод hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Возвращает логическое значение, указывающее, содержит ли объект свойство с указанным именем.|  
|[Метод isPrototypeOf](../../javascript/reference/isprototypeof-method-object-javascript.md)|Возвращает логическое значение, указывающее, существует ли объект в другом объекте цепочки прототипов.|  
|[Метод propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Возвращает логическое значение, определяющее, является ли указанное свойство частью объекта, и является ли оно перечислимым.|  
|[Метод setDate](../../javascript/reference/setdate-method-date-javascript.md)|Задает числовое значение дня месяца с помощью локального времени.|  
|[Метод setFullYear](../../javascript/reference/setfullyear-method-date-javascript.md)|Задает значение года, с помощью локального времени.|  
|[Метод setHours](../../javascript/reference/sethours-method-date-javascript.md)|Задает значение часов с помощью локального времени.|  
|[Метод setMilliseconds](../../javascript/reference/setmilliseconds-method-date-javascript.md)|Устанавливает значение миллисекунд с помощью локального времени.|  
|[Метод setMinutes](../../javascript/reference/setminutes-method-date-javascript.md)|Задает значение минут с помощью локального времени.|  
|[Метод setMonth](../../javascript/reference/setmonth-method-date-javascript.md)|Устанавливает значение месяца с помощью локального времени.|  
|[Метод setSeconds](../../javascript/reference/setseconds-method-date-javascript.md)|Задает значение, с помощью локального времени секунд.|  
|[Метод setTime](../../javascript/reference/settime-method-date-javascript.md)|Задает значение даты и времени в `Date` объекта.|  
|[Метод setUTCDate](../../javascript/reference/setutcdate-method-date-javascript.md)|Задает числовое значение дня месяца, в формате UTC.|  
|[Метод setUTCFullYear](../../javascript/reference/setutcfullyear-method-date-javascript.md)|Задает значение года, в формате UTC.|  
|[Метод setUTCHours](../../javascript/reference/setutchours-method-date-javascript.md)|Задает значение часов, в формате UTC.|  
|[Метод setUTCMilliseconds](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)|Устанавливает значение миллисекунд, в формате UTC.|  
|[Метод setUTCMinutes](../../javascript/reference/setutcminutes-method-date-javascript.md)|Задает значение минут, в формате UTC.|  
|[Метод setUTCMonth](../../javascript/reference/setutcmonth-method-date-javascript.md)|Устанавливает значение месяца, в формате UTC.|  
|[Метод setUTCSeconds](../../javascript/reference/setutcseconds-method-date-javascript.md)|Задает значение, в формате UTC секунд.|  
|[Метод setYear](../../javascript/reference/setyear-method-date-javascript.md)|Задает значение года, с помощью локального времени.|  
|[Метод toDateString](../../javascript/reference/todatestring-method-date-javascript.md)|Возвращает дату в виде строкового значения.|  
|[Метод toGMTString](../../javascript/reference/togmtstring-method-date-javascript.md)|Возвращает дату, преобразованную в строку с помощью среднего времени по Гринвичу (GMT).|  
|[Метод toISOString](../../javascript/reference/toisostring-method-date-javascript.md)|Возвращает дату в виде строкового значения в формате ISO.|  
|[Метод toJSON](../../javascript/reference/tojson-method-date-javascript.md)|Используется для преобразования данных типа объекта перед выполнением сериализации JSON.|  
|[Метод toLocaleDateString](../../javascript/reference/tolocaledatestring-method-date-javascript.md)|Возвращает дату в виде значение строки, подходящие для текущего языкового стандарта хост-среды.|  
|[Метод toLocaleString](../../javascript/reference/tolocalestring-date.md)|Возвращает объект, преобразованный в строку, используя текущий языковой стандарт.|  
|[Метод toLocaleTimeString](../../javascript/reference/tolocaletimestring-method-date-javascript.md)|Возвращает время в виде строкового значения подходящим для текущего языкового стандарта хост-среды.|  
|[Метод toString](../../javascript/reference/tostring-method-date.md)|Возвращает строковое представление объекта.|  
|[Метод toTimeString](../../javascript/reference/totimestring-method-date-javascript.md)|Возвращает время в виде строкового значения.|  
|[Метод toUTCString](../../javascript/reference/toutcstring-method-date-javascript.md)|Возвращает дату, преобразованную в строку в формате UTC.|  
|[Метод valueOf](../../javascript/reference/valueof-method-date.md)|Возвращает примитивное значение указанного объекта.|  
  
## <a name="see-also"></a>См. также  
 [Вычисление даты и времени (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)   
 [Строки даты и времени](../../javascript/date-and-time-strings-javascript.md)