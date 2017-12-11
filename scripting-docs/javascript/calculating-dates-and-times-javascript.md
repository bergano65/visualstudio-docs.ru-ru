---
title: "Вычисление даты и времени (JavaScript) | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- date and time arithmetic [JavaScript]
- JavaScript, date and time
- date comparison [JavaScript]
- date and time calculations [JavaScript]
ms.assetid: ea976f78-d934-479b-9056-880390d8bddd
caps.latest.revision: "34"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 18b4ff307c8f2c48a37ed9ca50e7c5f1ff693ece
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="calculating-dates-and-times-javascript"></a>Вычисление даты и времени (JavaScript)
[Объект Date](../javascript/reference/date-object-javascript.md) можно использовать для выполнения общих задач, связанных с календарем и часами, например для сравнения дат и вычисления затраченного времени.  
  
## <a name="setting-a-date-to-the-current-date"></a>Установка текущей даты  
 При создании экземпляра [объекта Date](../javascript/reference/date-object-javascript.md) без указания даты он возвращает значение, представляющее текущие дату и время, включая год, месяц, день, час, минуты, секунды и миллисекунды. В дальнейшем эти дату и время можно считывать и изменять.  
  
 Следующий пример показывает создание даты без использования параметров и ее отображение в формате *мм-дд-гг*.  
  
```JavaScript  
var dt = new Date();  
  
// Display the month, day, and year. getMonth() returns a 0-based number.  
var month = dt.getMonth()+1;  
var day = dt.getDate();  
var year = dt.getFullYear();  
document.write(month + '-' + day + '-' + year);  
  
// Output: current month, day, year  
```  
  
## <a name="setting-a-specific-date"></a>Установка определенной даты  
 Конкретную дату можно задать, передав строку даты в конструктор.  
  
```JavaScript  
var dt = new Date('8/24/2009');  
document.write(dt);  
  
// Output: Mon Aug 24 00:00:00 PDT 2009  
  
```  
  
> [!IMPORTANT]
>  Часовой пояс, отображаемый в строке даты, соответствует установленному на локальном компьютере.  
>   
>  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] позволяет гибко задавать формат строки, используемой в качестве параметра. Например, можно ввести "8-24-2009", "24 августа 2009" или "24 авг 2009".  
  
 Можно также указать время. В следующем примере показан один из способов задания даты и времени в формате ISO. "Z" означает время в формате UTC.  
  
```JavaScript  
var dt = new Date('2010-06-09T15:20:00Z');  
document.write(dt);  
document.write("<br />");  
document.write(dt.toISOString());  
  
// Output:  
// Wed Jun 09 2010 08:20:00 GMT-0700 (Pacific Daylight Time)  
// 2010-06-09T15:20:00.000Z  
```  
  
 Дополнительные сведения о форматах даты, в частности о формате ISO, см. в разделе [Строки даты и времени](../javascript/date-and-time-strings-javascript.md).  
  
 В следующем примере показаны другие способы задания времени.  
  
```JavaScript  
var dtA = new Date('8/24/2009 14:52:10');  
  
// The parameters are year, month, day, hours, minutes, seconds.  
var dtB = new Date(2009, 7, 24, 14, 52, 10);  
document.write(dtA);  
document.write("<br/>");  
document.write(dtB);  
  
// Output:  
// Mon Aug 24 14:52:10 PDT 2009  
// Mon Aug 24 14:52:10 PDT 2009  
  
```  
  
## <a name="adding-and-subtracting-days-months-and-years"></a>Добавление и вычитание дней, месяцев и лет  
 Для задания определенных дат и времени можно использовать методы getX и setX объекта `Date`.  
  
 В следующем примере показано, как установить в качестве даты предыдущий день. Обратите внимание, что при необходимости значения месяца и года также можно изменить.  
  
```JavaScript  
var myDate = new Date("1/1/1990");  
var dayOfMonth = myDate.getDate();  
myDate.setDate(dayOfMonth - 1);  
  
document.write(myDate);  
  
// Output: Sun Dec 31 00:00:00 PST 1989  
```  
  
 В следующем примере в качестве даты задается последний день месяца путем вычитания одного дня из первого дня следующего месяца.  
  
> [!TIP]
>  Месяцы года нумеруются от 0 (январь) до 11 (декабрь), а недели — от 0 (воскресенье) до 6 (суббота).  
  
```JavaScript  
var myDate = new Date("1/1/1990")  
myDate.setMonth(myDate.getMonth() + 1);  
  
myDate.setDate (myDate.getDate() - 1);  
  
document.write(myDate);  
  
// Output: Wed Jan 31 00:00:00 PST 1990  
  
```  
  
## <a name="working-with-days-of-the-week"></a>Работа с днями недели  
 [Метод getDay](../javascript/reference/getday-method-date-javascript.md) получает день недели в виде числа от 0 (воскресенье) до 6 (суббота). (Он отличается от [метода getDate](../javascript/reference/getdate-method-date-javascript.md), получающего день месяца в виде числа от 1 до 31.)  
  
 В следующем примере в качестве даты задается День благодарения, который в США приходится на четвертый четверг ноября. Скрипт находит 1 ноября текущего года, затем первый четверг и прибавляет три недели.  
  
```JavaScript  
var myDate = new Date();  
myDate.setHours(0, 0, 0, 0);  
  
myDate.setYear(2013);  
  
// Determine November 1.  
myDate.setDate(1);  
myDate.setMonth(10);  
  
// Find Thursday.  
var thursday = 4;  
while(myDate.getDay() != thursday) {  
    myDate.setDate(myDate.getDate() + 1);  
}  
  
// Add 3 weeks.  
myDate.setDate(myDate.getDate() + 21);  
  
document.write(myDate);  
  
// Output: Thu Nov 28 00:00:00 <time zone> 2013  
  
```  
  
## <a name="calculating-elapsed-time"></a>Подсчет затраченного времени  
 [Метод getTime](../javascript/reference/gettime-method-date-javascript.md) возвращает число миллисекунд, прошедших с полуночи 1 января 1970 года. Для любой даты до этой он возвращает отрицательное число.  
  
 [Метод getTime](../javascript/reference/gettime-method-date-javascript.md) можно использовать для задания начального и конечного времени при вычислении затраченного времени. Это можно использовать для измерения коротких единиц, таких как несколько секунд, и больших единиц, таких как дни.  
  
 В следующем примере вычисляется истекшее время в секундах. [Метод getTime](../javascript/reference/gettime-method-date-javascript.md) получает число миллисекунд, прошедших с нулевой даты.  
  
```JavaScript  
var startTime = new Date('1/1/1990');  
var startMsec = startTime.getMilliseconds();  
startTime.setTime(5000000);  
var elapsed = (startTime.getTime() - startMsec) / 1000;   
document.write(elapsed);  
  
// Output: 5000  
  
```  
  
 Чтобы работать с единицами, которыми легче управлять, можно разделить миллисекунды, предоставленные [методом getTime](../javascript/reference/gettime-method-date-javascript.md), на соответствующее число. Например, для преобразования миллисекунд в дни разделите их количество на 86 400 000 (1000 миллисекунд x 60 секунд x 60 минут x 24 часа).  
  
 В следующем примере показывается, сколько времени прошло с первого дня заданного года. Для вычисления истекшего времени в днях, часах, минутах и секундах используются операции деления. Летнее время не принято во внимание.  
  
```JavaScript  
// Set the unit values in milliseconds.  
var msecPerMinute = 1000 * 60;  
var msecPerHour = msecPerMinute * 60;  
var msecPerDay = msecPerHour * 24;  
  
// Set a date and get the milliseconds  
var date = new Date('6/15/1990');  
var dateMsec = date.getTime();  
  
// Set the date to January 1, at midnight, of the specified year.  
date.setMonth(0);  
date.setDate(1);  
date.setHours(0, 0, 0, 0);  
  
// Get the difference in milliseconds.  
var interval = dateMsec - date.getTime();  
  
// Calculate how many days the interval contains. Subtract that  
// many days from the interval to determine the remainder.  
var days = Math.floor(interval / msecPerDay );  
interval = interval - (days * msecPerDay );  
  
// Calculate the hours, minutes, and seconds.  
var hours = Math.floor(interval / msecPerHour );  
interval = interval - (hours * msecPerHour );  
  
var minutes = Math.floor(interval / msecPerMinute );  
interval = interval - (minutes * msecPerMinute );  
  
var seconds = Math.floor(interval / 1000 );  
  
// Display the result.  
document.write(days + " days, " + hours + " hours, " + minutes + " minutes, " + seconds + " seconds.");  
  
//Output: 164 days, 23 hours, 0 minutes, 0 seconds.  
```  
  
### <a name="determining-the-users-age"></a>Определение возраста пользователя  
 В следующем примере берется день рождения пользователя и вычисляется его возраст. Год рождения вычитается из текущего года, и из получившегося результата вычитается 1, если день рождения в текущем году еще не наступил.  
  
```JavaScript  
var birthday = new Date("8/1/1985");  
var today = new Date();  
var years = today.getFullYear() - birthday.getFullYear();  
  
// Reset birthday to the current year.  
birthday.setFullYear(today.getFullYear());  
  
// If the user's birthday has not occurred yet this year, subtract 1.  
if (today < birthday)  
{  
    years--;  
}  
document.write("You are " + years + " years old.");  
  
// Output: You are <number of years> years old.  
  
```  
  
## <a name="comparing-dates"></a>Сравнение дат  
 При сравнении дат в [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] необходимо иметь в виду, что оператор `==` возвращает значение `true`, только если даты с его обеих сторон относятся к одному и тому же объекту. Поэтому при наличии двух отдельных объектов `Date`, для которых задана одна и та же дата, оператор `date1 == date2` возвращает значение `false`. Кроме того, объект `Date`, для которого задана дата, но не задано время, инициализируется с использованием времени, соответствующим полуночи заданной даты. Поэтому при сравнении объекта `Date`, установленного без заданного времени, например, с объектом `Date.now`, необходимо учитывать, что для объекта `Date` устанавливается значение полуночи, а для объекта `Date.now` такое значение не устанавливается.  
  
 В следующем примере проверяется, совпадает ли текущая дата с заданной, предшествует ли ей или следует после нее. Для установки текущей даты в `todayAtMidn` скрипт создает объект `Date` для текущего года, месяца и дня.  
  
```JavaScript  
// Get the current date at midnight.  
var now = new Date();   
var todayAtMidn = new Date(now.getFullYear(), now.getMonth(), now.getDate());  
  
// Set specificDate to a specified date at midnight.  
var specificDate = new Date("9/21/2009");  
  
// Compare the two dates by comparing the millisecond  
// representations.  
if (todayAtMidn.getTime() == specificDate.getTime())  
{  
    document.write("Same");  
}  
else  
{  
    document.write("Different");  
}  
  
//Output: Different  
```  
  
 Изменив предыдущий пример, можно проверить, находится ли предоставленная дата в пределах конкретного диапазона.  
  
```JavaScript  
// Get the current date at midnight.  
var now = new Date();  
var todayAtMidn = new Date(now.getFullYear(), now.getMonth(), now.getDate());  
  
// Set start/end dates to a specified date (ISO format).  
var startDate = new Date("2009-06-09T15:20:00Z");  
var endDate = new Date("2011-06-09T15:20:00Z");  
  
// Compare the two dates by comparing the millisecond  
// representations.  
if (todayAtMidn.getTime() > startDate.getTime() &&   
    todayAtMidn.getTime() < endDate.getTime()) {  
    document.write("Specified date is within this range.");  
}  
else {  
    document.write("Specified date is not in this range.");  
}  
  
// Output: Specified date is not in this range.  
```  
  
## <a name="see-also"></a>См. также  
 [Объект Date](../javascript/reference/date-object-javascript.md)