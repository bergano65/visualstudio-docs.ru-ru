---
title: "Строки даты и времени (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: ba0798c5-3574-4434-89f4-3d90be276001
caps.latest.revision: 47
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 47
---
# Строки даты и времени (JavaScript)
Для задания и форматирования строк дат и времени в JavaScript можно использовать несколько методов.  
  
## Форматирование дат с помощью объекта Intl.DateTimeFormat  
 В Internet Explorer 11 представлена поддержка формата [Объект Intl.DateTimeFormat](../javascript/reference/intl-datetimeformat-object-javascript.md), который входит в [Спецификацию API интернационализации ECMAScript](http://www.ecma-international.org/ecma-402/1.0/).  Для форматирования дат можно использовать непосредственно этот объект или обновленную реализацию методов [Метод toLocaleDateString \(Date\)](../javascript/reference/tolocaledatestring-method-date-javascript.md) и [Метод toLocaleTimeString \(Date\)](../javascript/reference/tolocaletimestring-method-date-javascript.md).  Эти методы объекта [Объект Date](../javascript/reference/date-object-javascript.md) используют объект `Intl.DateTimeFormat` внутренне для поддержки новых необязательных параметров языкового стандарта и других параметров форматирования.  
  
 В следующем примере показано использование `toLocaleDateString` и `toLocaleTimeString` для форматирования дат и времени.  Первый параметр, передаваемый для этих методов, — значение языкового стандарта, например en\-us.  Второй параметр \(если он присутствует\) определяет параметры форматирования, например длинное представление дня недели.  
  
```javascript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = {  
    weekday: "long", year: "numeric", month: "short",  
    day: "numeric", hour: "2-digit", minute: "2-digit"  
};  
  
document.write(date.toLocaleDateString("en-US"));  
document.write(date.toLocaleTimeString("en-us", options));  
document.write(date.toLocaleDateString("ja-JP"));  
document.write(date.toLocaleTimeString("ja-JP", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013  
// ‎Friday‎, ‎Feb‎ ‎1‎, ‎2013‎ ‎06‎:‎00‎ ‎AM  
// ‎2013‎年‎2‎月‎1‎日‎  
// ‎2013‎年‎2‎月‎1‎日 ‎金曜日‎ ‎06‎:‎00  
```  
  
 Полный список параметров форматирования см. в разделе [Объект Intl.DateTimeFormat](../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
## Форматирование дат  
 До Internet Explorer 11 в JavaScript не было специальных методов форматирования дат и времени.  Чтобы обеспечить собственное форматирование дат для предыдущих версий браузера, используйте методы [Метод getDay \(Date\)](../javascript/reference/getday-method-date-javascript.md), [Метод getDate \(Date\)](../javascript/reference/getdate-method-date-javascript.md), [Метод getMonth \(Date\)](../javascript/reference/getmonth-method-date-javascript.md) и [Метод getFullYear \(Date\)](../javascript/reference/getfullyear-method-date-javascript.md).  \(Метод [Метод getYear \(Date\)](../javascript/reference/getyear-method-date-javascript.md) устарел и использовать его не следует.\)  
  
```javascript  
var myDate = new Date("February 3, 2001");  
var myDate = new Date("February 3 2001");  
document.write((myDate.getMonth() + 1) + "-" + myDate.getDate() + "-" + myDate.getFullYear());  
document.write("<br/>");  
document.write((myDate.getMonth() + 1) + "/" + myDate.getDate() + "/" + myDate.getFullYear());  
  
//Output:  
// 2-3-2001  
// 2/3/2001  
```  
  
 Собственное форматирование времени можно обеспечить с помощью методов [Метод getHours \(Date\)](../javascript/reference/gethours-method-date-javascript.md), [Метод getMinutes \(Date\)](../javascript/reference/getminutes-method-date-javascript.md), [Метод getSeconds \(Date\)](../javascript/reference/getseconds-method-date-javascript.md) и [Метод getMilliseconds \(Date\)](../javascript/reference/getmilliseconds-method-date-javascript.md).  
  
```javascript  
myDate = new Date();  
myDate.setHours(10, 30, 53, 400);  
  
document.write(myDate.getHours() + ":" + myDate.getMinutes() + ":" + myDate.getSeconds() +  
":" + myDate.getMilliseconds());  
  
// Output:  
// 10:30:53:400  
```  
  
## Преобразование строк в даты  
 Строки для создания объектов `Date` можно также задавать с помощью функций `Date(dateStr)` или `Date.parse(dateStr)`.  JavaScript использует следующие правила анализа строк даты.  
  
-   Сначала выполняется попытка анализа строки даты, используя [Формат даты ISO](#ISO).  
  
    > [!NOTE]
    >  JavaScript использует упрощенную версию расширенного формата ISO 8601.  
  
-   Если строка даты не в формате ISO, JavaScript пытается выполнить анализ даты, используя другие [Другие форматы даты](#OtherDateFormats).  
  
<a name="ISO"></a>   
## Формат даты ISO  
 Формат ISO — это упрощение расширенного формата ISO 8601.  Он следующий:  
  
 `YYYY-MM-DDTHH:mm:ss.sssZ`  
  
> [!IMPORTANT]
>  В Internet Explorer 8 \(в стандартном режиме и режиме совместимости\) формат даты ISO не поддерживается.  
  
 В следующей таблице описаны компоненты этого формата.  
  
|Символ|Описание|Значения|  
|------------|--------------|--------------|  
|`-`, `:`, `.`, `T`|Фактические символы строки.  `T` указывает точку отсчета времени.||  
|`YYYY`|Год.  Вместо 4\-значного представления года может использоваться расширенное представление.  Дополнительные сведения см. в разделе [Расширенные года](../javascript/date-and-time-strings-javascript.md#bkmk_extend) далее в этой статье.||  
|`MM`|Месяц.|От 01 до 12|  
|`DD`|День месяца.|От 01 до 31|  
|`HH`|Часы.|От 00 до 24|  
|`mm`|Минуты.|От 00 до 59|  
|`ss`|Секунды.  При задании времени указывать секунды и миллисекунды необязательно.|От 00 до 59|  
|`sss`|Milliseconds|От 00 до 999|  
|`Z`|Значение в этой позиции может быть одним из указанных ниже.  Если значение не задано, используется время в формате UTC.<br /><br /> -   `Z` означает время в формате UTC.<br />-   `+hh:mm` означает, что введенное время представляет собой смещение относительно времени в формате UTC в сторону увеличения.<br />-   `-hh:mm` означает, что введенное время представляет абсолютное значение указанного смещения относительно времени в формате UTC в сторону уменьшения.||  
  
 Строка может содержать только дату, как в следующих форматах: `YYYY`, `YYYY-MM`, `YYYY-MM-DD`.  
  
 В формате ISO имена часовых поясов не поддерживаются.  Для задания смещения относительно времени в формате UTC можно использовать позицию `Z`.  Если значение в позиции `Z` не указано, используется время в формате UTC.  
  
 Полночь можно указать значением 00:00:00 или значением 24:00:00 предыдущего дня.  Следующие две строки определяют одно и то же время: 2010\-05\-25T00:00 и 2010\-05\-24T24:00.  
  
 Чтобы вернуть дату в формате ISO, можно использовать [Метод toISOString \(Date\)](../javascript/reference/toisostring-method-date-javascript.md).  
  
<a name="bkmk_extend"></a>   
### Расширенные года  
 *Расширенный формат года* содержит 6 цифр вместо 4 с предшествующим знаком плюс или минус.  Пример расширенного представления года — `+002010`. Это представление эквивалентно представлению `2010`.  Такой расширенный формат можно использовать для представления года до 0\-го и после 9999\-го.  
  
 При использовании 6\-значного формата должен присутствовать знак плюс или минус.  При использовании 4\-значного формата знака быть не должно.  Следовательно, значения `0000` и `+000000` допустимы, а значения `000000` и `-0001` приводят к ошибке.  Расширенное представление года 0 считается положительным и поэтому в качестве префикса для него используется знак плюс.  
  
 Для представления года до 0\-го и после 9999\-го [Метод toISOString \(Date\)](../javascript/reference/toisostring-method-date-javascript.md) всегда использует расширенный формат.  
  
> [!NOTE]
>  [!INCLUDE[jsv9](../javascript/includes/jsv9-md.md)]  
  
<a name="OtherDateFormats"></a>   
## Другие форматы даты  
 Если строка даты имеет формат, отличный от формата ISO, в [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] используются следующие правила ее анализа.  
  
 Краткие форматы даты  
  
-   Формат должен быть следующий: месяц\/день\/год, например 06\/08\/2010.  
  
-   В качестве разделителя может использоваться символ «\/» или «\-».  
  
 Длинные форматы даты  
  
-   Год, месяц и день могут размещаться в любом порядке. "  Например, допустимы значения June 8 2010 и 2010 June 8.  
  
-   Год может содержать две или четыре цифры.  Если год содержит только две цифры, он должен быть не ранее 70\-го.  
  
-   Имена месяцев и дней должны содержать не менее двух знаков.  Неуникальные двузначные имена преобразуются в последнее соответствующее имя.  Например, Ju означает июль, а не июнь.  
  
-   Если день недели не совместим с остальной частью указанной даты, он игнорируется.  Например, Tuesday November 9 1996 преобразуется в Friday November 9 1996, поскольку правильный день недели для этой даты — пятница.  
  
 Форматы времени  
  
-   Часы, минуты и секунды разделяются символом двоеточия.  Некоторые компоненты можно опускать.  Допустимы следующие значения: «10:», «10:11» и «10:11:12».  
  
-   Если указано PM и задан час не менее 13, возвращается значение NaN.  Например, при задании «23:15 PM» возвращается значение NaN.  
  
 Общие правила  
  
-   Строка, содержащая недопустимое значение даты, возвращает значение NaN.  Например, строка, содержащая два года или два месяца, возвращает значение NaN.  
  
-   В [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] поддерживаются все стандартные часовые пояса, время в формате UTC и время по Гринвичу \(GMT\).  \(В формате ISO часовые пояса не поддерживаются.\)  
  
-   Текст, заключенный в скобки, считается комментарием.  Скобки могут быть вложенными.  
  
-   Запятые и пробелы считаются разделителями.  Разрешается использовать несколько разделителей.  
  
## Пример  
 В следующем примере кода отображаются результаты синтаксического анализа разных строк дат и времени.  
  
```  
document.writeln((new Date("2010")).toUTCString());  
  
document.writeln((new Date("2010-06")).toUTCString());  
  
document.writeln((new Date("2010-06-09")).toUTCString());  
  
 // Specifies Z, which indicates UTC time.  
document.writeln((new Date("2010-06-09T15:20:00Z")).toUTCString());  
  
 // Specifies -07:00 offset, which is equivalent to Pacific Daylight time.  
document.writeln((new Date("2010-06-09T15:20:00-07:00")).toGMTString());  
  
// Specifies a non-ISO Long date.  
document.writeln((new Date("June 9, 2010")).toUTCString());  
  
// Specifies a non-ISO Long date.  
document.writeln((new Date("2010 June 9")).toUTCString());  
  
// Specifies a non-ISO Short date and time.  
document.writeln((new Date("6/9/2010 3:20 pm")).toUTCString());  
  
// Output:  
// Fri, 1 Jan 2010 00:00:00 UTC  
// Tue, 1 Jun 2010 00:00:00 UTC  
// Wed, 9 Jun 2010 00:00:00 UTC  
// Wed, 9 Jun 2010 15:20:00 UTC  
// Wed, 9 Jun 2010 22:20:00 UTC  
// Wed, 9 Jun 2010 07:00:00 UTC  
// Wed, 9 Jun 2010 07:00:00 UTC  
// Wed, 9 Jun 2010 22:20:00 UTC  
```  
  
 Если указывается местное время, результат зависит от часового пояса.  
  
> [!IMPORTANT]
>  В Internet Explorer 8 \(в стандартном режиме и режиме совместимости\) формат даты ISO не поддерживается.  
  
## См. также  
 [Объект Date](../javascript/reference/date-object-javascript.md)   
 [Функция Date.parse](../javascript/reference/date-parse-function-javascript.md)