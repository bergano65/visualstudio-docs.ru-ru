---
title: "Объект Date (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Date"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date - объект"
  - "даты, определение"
ms.assetid: ce2202bb-7ec9-4f5a-bf48-3a04feff283e
caps.latest.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 29
---
# Объект Date (JavaScript)
Обеспечивает основные возможности сохранения и извлечения даты и времени.  
  
## Синтаксис  
  
```  
  
      dateObj = new Date()  
dateObj = new Date(dateVal)  
dateObj = new Date(year, month, date[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## Параметры  
 `dateObj`  
 Обязательное.  Имя переменной, которой присваивается объект `Date`.  
  
 `dateVal`  
 Обязательное.  В случае числового значения параметр `dateVal` представляет количество миллисекунд в формате UTC между указанной датой и полуночью 1 января 1970 г.  В случае строкового значения параметр `dateVal` анализируется в соответствии с правилами, приведенными в разделе [Строки даты и времени](../../javascript/date-and-time-strings-javascript.md).  Аргумент `dateVal` также может быть значением VT\_DATE, возвращаемым некоторыми объектами ActiveX.  
  
 `year`  
 Обязательное.  Полное представление года, например 1976 \(а не 76\).  
  
 `month`  
 Обязательное.  Месяц, представляемый в виде числа от 0 до 11 \(с января по декабрь\).  
  
 `date`  
 Обязательное.  Дата в виде целого числа в диапазоне от 1 до 31.  
  
 `hours`  
 Необязательный параметр.  Необходимо задавать, если задается значение `minutes`.  Целое число от 0 до 23 \(от полуночи до 23:00\), представляющее час.  
  
 минуты  
 Необязательный параметр.  Необходимо задавать, если задается значение `seconds`.  Целое число от 0 до 59, представляющее минуты.  
  
 `seconds`  
 Необязательный параметр.  Необходимо задавать, если задается значение `milliseconds`.  Целое число от 0 до 59, представляющее секунды.  
  
 `ms`  
 Необязательный параметр.  Целое число от 0 до 999, представляющее миллисекунды.  
  
## Заметки  
 Объект `Date` содержит число, представляющее определенный момент времени с точностью до миллисекунды.  Если значение аргумента превышает верхнюю границу его диапазона или является отрицательным числом, остальные хранящиеся значения изменяются соответственно.  Например, если задать 150 секунд, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] переопределит это число как две минуты и 30 секунд.  
  
 Если число равно `NaN`, объект не представляет конкретный момент времени.  Если не передавать параметры объекту `Date`, он инициализируется текущим временем \(UTC\).  Перед использованием этого объекта ему необходимо присвоить значение.  
  
 Диапазон дат, которые могут быть представлены объектом `Date`, составляет около 285 616 в каждую сторону от 1 января 1970 г.  
  
 См. в [Вычисление даты и времени \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md) дополнительные сведения об использовании объекта `Date` и связанных с ним методов.  
  
## Пример  
 В следующем примере показано использование объекта `Date`.  
  
```javascript  
var dateString = "Today's date is: ";  
  
var newDate = new Date();  
  
// Get the month, day, and year.  
dateString += (newDate.getMonth() + 1) + "/";  
dateString += newDate.getDate() + "/";  
dateString += newDate.getFullYear();  
  
document.write(dateString);  
  
// Output: Today's date is: <date>  
```  
  
## Требования  
 `Date object` был введен в [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)].  Некоторые члены в следующих списках были введены в более поздних версиях.  Дополнительные сведения см. в разделе [Сведения о версии](../../javascript/reference/javascript-version-information.md) или в документации по отдельным членам.  
  
## Свойства  
 В следующей таблице перечислены свойства `Date Object`.  
  
|Свойство|Описание|  
|--------------|--------------|  
|[Свойство сonstructor](../../javascript/reference/constructor-property-date.md)|Указывает функцию, которая создает объект.|  
|[Свойство prototype](../../javascript/reference/prototype-property-date.md)|Возвращает ссылку на прототип класса объектов.|  
  
## Функции  
 В следующей таблице перечислены функции `Date Object`.  
  
|Функции|Описание|  
|-------------|--------------|  
|[Функция Date.now](../../javascript/reference/date-now-function-javascript.md)|Возвращает число миллисекунд между 1 января 1970 г. и текущими датой и временем.|  
|[Функция Date.parse](../../javascript/reference/date-parse-function-javascript.md)|Выполняет синтаксический анализ строки, содержащей дату, и возвращает количество миллисекунд, истекших с полуночи 1 января 1970 г.|  
|[Функция Date.UTC](../../javascript/reference/date-utc-function-javascript.md)|Возвращает количество миллисекунд, истекших с полуночи 1 января 1970 года до указанной даты, используя время в формате UTC \(или время GMT\).|  
  
<a name="js56jsobjdatemeth"></a>   
## Методы  
 В следующей таблице перечислены методы `Date Object`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Метод getDate](../../javascript/reference/getdate-method-date-javascript.md)|Возвращает значение дня месяца, используя местное время.|  
|[Метод getDay](../../javascript/reference/getday-method-date-javascript.md)|Возвращает значение дня недели, используя местное время.|  
|[Метод getFullYear](../../javascript/reference/getfullyear-method-date-javascript.md)|Возвращает значение года, используя местное время.|  
|[Метод getHours](../../javascript/reference/gethours-method-date-javascript.md)|Возвращает значение часов, используя местное время.|  
|[Метод getMilliseconds](../../javascript/reference/getmilliseconds-method-date-javascript.md)|Возвращает значение миллисекунд, используя местное время.|  
|[Метод getMinutes](../../javascript/reference/getminutes-method-date-javascript.md)|Возвращает значение минут, используя местное время.|  
|[Метод getMonth](../../javascript/reference/getmonth-method-date-javascript.md)|Возвращает значение месяца, используя местное время.|  
|[Метод getSeconds](../../javascript/reference/getseconds-method-date-javascript.md)|Возвращает значение секунд, используя местное время.|  
|[Метод getTime](../../javascript/reference/gettime-method-date-javascript.md)|Возвращает значение времени в объекте `Date` в виде количества миллисекунд, истекших с полуночи 1 января 1970 г.|  
|[Метод getTimezoneOffset](../../javascript/reference/gettimezoneoffset-method-date-javascript.md)|Возвращает разницу в минутах между временем на локальном компьютере и временем в формате UTC.|  
|[Метод getUTCDate](../../javascript/reference/getutcdate-method-date-javascript.md)|Возвращает значение дня месяца, используя время в формате UTC.|  
|[Метод getUTCDay](../../javascript/reference/getutcday-method-date-javascript.md)|Возвращает значение дня недели, используя время в формате UTC.|  
|[Метод getUTCFullYear](../../javascript/reference/getutcfullyear-method-date-javascript.md)|Возвращает значение года, используя время в формате UTC.|  
|[Метод getUTCHours](../../javascript/reference/getutchours-method-date-javascript.md)|Возвращает значение часов, используя время в формате UTC.|  
|[Метод getUTCMilliseconds](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)|Возвращает значение миллисекунд, используя время в формате UTC.|  
|[Метод getUTCMinutes](../../javascript/reference/getutcminutes-method-date-javascript.md)|Возвращает значение минут, используя время в формате UTC.|  
|[Метод getUTCMonth](../../javascript/reference/getutcmonth-method-date-javascript.md)|Возвращает значение месяца, используя время в формате UTC.|  
|[Метод getUTCSeconds](../../javascript/reference/getutcseconds-method-date-javascript.md)|Возвращает значение секунд, используя время в формате UTC.|  
|[Метод getVarDate](../../javascript/reference/getvardate-method-date-javascript.md)|Возвращает значение VT\_DATE в объекте `Date`.|  
|[Метод getYear](../../javascript/reference/getyear-method-date-javascript.md)|Возвращает значение года.|  
|[Метод hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Возвращает логическое значение, указывающее, содержит ли объект свойство с указанным именем.|  
|[Метод isPrototypeOf](../../javascript/reference/isprototypeof-method-object-javascript.md)|Возвращает логическое значение, указывающее, существует ли объект в другом объекте цепочки прототипов.|  
|[Метод propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Возвращает логическое значение, определяющее, является ли указанное свойство частью объекта, и является ли оно перечислимым.|  
|[Метод setDate](../../javascript/reference/setdate-method-date-javascript.md)|Задает числовой день месяца, используя местное время.|  
|[Метод setFullYear](../../javascript/reference/setfullyear-method-date-javascript.md)|Задает значение года, используя местное время.|  
|[Метод setHours](../../javascript/reference/sethours-method-date-javascript.md)|Задает значение часов, используя местное время.|  
|[Метод setMilliseconds](../../javascript/reference/setmilliseconds-method-date-javascript.md)|Задает значение миллисекунд, используя местное время.|  
|[Метод setMinutes](../../javascript/reference/setminutes-method-date-javascript.md)|Задает значение минут, используя местное время.|  
|[Метод setMonth](../../javascript/reference/setmonth-method-date-javascript.md)|Задает значение месяца, используя местное время.|  
|[Метод setSeconds](../../javascript/reference/setseconds-method-date-javascript.md)|Задает значение секунд, используя местное время.|  
|[Метод setTime](../../javascript/reference/settime-method-date-javascript.md)|Устанавливает значение даты и времени в объекте `Date`.|  
|[Метод setUTCDate](../../javascript/reference/setutcdate-method-date-javascript.md)|Задает числовой день месяца, используя время в формате UTC.|  
|[Метод setUTCFullYear](../../javascript/reference/setutcfullyear-method-date-javascript.md)|Задает значение года, используя время в формате UTC.|  
|[Метод setUTCHours](../../javascript/reference/setutchours-method-date-javascript.md)|Задает значение часов, используя время в формате UTC.|  
|[Метод setUTCMilliseconds](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)|Задает значение миллисекунд, используя время в формате UTC.|  
|[Метод setUTCMinutes](../../javascript/reference/setutcminutes-method-date-javascript.md)|Задает значение минут, используя время в формате UTC.|  
|[Метод setUTCMonth](../../javascript/reference/setutcmonth-method-date-javascript.md)|Задает значение месяца, используя время в формате UTC.|  
|[Метод setUTCSeconds](../../javascript/reference/setutcseconds-method-date-javascript.md)|Задает значение секунд, используя время в формате UTC.|  
|[Метод setYear](../../javascript/reference/setyear-method-date-javascript.md)|Задает значение года, используя местное время.|  
|[Метод toDateString](../../javascript/reference/todatestring-method-date-javascript.md)|Возвращает дату в виде строкового значения.|  
|[Метод toGMTString](../../javascript/reference/togmtstring-method-date-javascript.md)|Возвращает дату, преобразованную в строку с помощью времени GMT.|  
|[Метод toISOString](../../javascript/reference/toisostring-method-date-javascript.md)|Возвращает дату в виде строкового значения в формате ISO.|  
|[Метод toJSON](../../javascript/reference/tojson-method-date-javascript.md)|Используется для преобразования данных типа объекта перед сериализацией JSON.|  
|[Метод toLocaleDateString](../../javascript/reference/tolocaledatestring-method-date-javascript.md)|Возвращает дату в виде строки, соответствующей текущему языковому стандарту хост\-среды.|  
|[Метод toLocaleString](../../javascript/reference/tolocalestring-date.md)|Возвращает объект, преобразованный в строку, используя текущий языковой стандарт.|  
|[Метод toLocaleTimeString](../../javascript/reference/tolocaletimestring-method-date-javascript.md)|Возвращает время в виде строки, соответствующей текущему языковому стандарту хост\-среды.|  
|[Метод toString](../../javascript/reference/tostring-method-date.md)|Возвращает строковое представление объекта.|  
|[Метод toTimeString](../../javascript/reference/totimestring-method-date-javascript.md)|Возвращает время в виде строкового значения.|  
|[Метод toUTCString](../../javascript/reference/toutcstring-method-date-javascript.md)|Возвращает дату, преобразованную в строку с использованием времени в формате UTC.|  
|[Метод valueOf](../../javascript/reference/valueof-method-date.md)|Возвращает примитивное значение указанного объекта.|  
  
## См. также  
 [Вычисление даты и времени \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md)   
 [Строки даты и времени](../../javascript/date-and-time-strings-javascript.md)