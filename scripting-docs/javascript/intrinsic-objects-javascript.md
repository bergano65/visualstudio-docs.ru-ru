---
title: "Встроенные объекты (JavaScript) | Документы Майкрософт"
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
- built-in objects [JavaScript]
- intrinsic objects [JavaScript]
ms.assetid: 6520c634-a7d1-4a05-8c1b-2e79f449d2e4
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 242b572c2818f9968e6d5fc51e1272e3004c0f05
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="intrinsic-objects-javascript"></a>Встроенные объекты (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] предоставляет встроенные объекты. Это объекты`Array`, `Boolean`, `Date`, `Error`, `Function`, **Global**, **JSON**, **Math**, **Number**, `Object`, `RegExp` и `String`. Встроенные объекты имеют связанные методы, функции, свойства и константы, которые подробно описаны в [справочнике по языку](../javascript/reference/javascript-reference.md).  
  
## <a name="array-object"></a>Объект Array  
 Нижние индексы массива можно рассматривать как свойства объекта и обращаться к ним по числовому индексу. Обратите внимание, что именованные свойства, добавленные в массив, нельзя индексировать по номеру; они стоят отдельно от элементов массива.  
  
 Чтобы создать массив, используйте оператор **new** и [конструктор](../javascript/reference/constructor-property-object-javascript.md) **Array()**, как показано в следующем примере.  
  
```JavaScript  
var theMonths = new Array(12);  
theMonths[0] = "Jan";  
theMonths[1] = "Feb";  
theMonths[2] = "Mar";  
theMonths[3] = "Apr";  
theMonths[4] = "May";  
theMonths[5] = "Jun";  
theMonths[6] = "Jul";  
theMonths[7] = "Aug";  
theMonths[8] = "Sep";  
theMonths[9] = "Oct";  
theMonths[10] = "Nov";  
theMonths[11] = "Dec";  
```  
  
 При создании массива с помощью ключевого слова `Array` [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] добавляет свойство **length**, регистрирующее число записей. Если значение этого свойства не задано, оно считается равным нулю, и массив не содержит элементов. Если значение указано, оно определяет длину массива. Если указано несколько параметров, они используются как элементы массива. Кроме того, число параметров присваивается свойству length. Это показано в следующем примере, который представляет собой эквивалент приведенного выше кода.  
  
```JavaScript  
var theMonths = new Array("Jan", "Feb", "Mar", "Apr", "May", "Jun",   
"Jul", "Aug", "Sep", "Oct", "Nov", "Dec");  
```  
  
 При добавлении элементов в массив, созданный с помощью ключевого слова `Array`, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] автоматически изменяет значение свойства **length**. Индексы массивов [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] всегда начинаются с 0, а не с 1, поэтому значение свойства length всегда на единицу превышает наибольший индекс массива.  
  
## <a name="string-object"></a>Объект String  
 В [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] со строками (и числами) можно обращаться так, как если бы они были объектами. [Объект String](../javascript/reference/string-object-javascript.md) имеет несколько встроенных методов, которые можно использовать для работы со строками. Одним из них является [метод substring](../javascript/reference/substring-method-string-javascript.md), возвращающий часть строки. В качестве аргументов он принимает два числа.  
  
```JavaScript  
var aString = "0123456789";  
  
// This code sets aChunk to "456".  
var aChunk = aString.substring(4, 7);  
  
// This code sets anotherChunk to "456", using  
// the lower value index as the starting index.  
var anotherChunk = aString.substring(7, 4);  
  
// This code sets the firstLetter variable to "J"  
// by using the array in the preceding array creation example.  
firstLetter = theMonths[5].substring(0,1);  
```  
  
 Другим свойством объекта `String` является **length**. Оно содержит число символов в строке (или 0 для пустой строки). Значение этого свойства выражается числом и может использоваться в вычислениях.  
  
```JavaScript  
var howLong = "Hello World".length  // Sets the howLong variable to 11.  
```  
  
## <a name="math-object"></a>Объект Math  
 Объект **Math** имеет ряд предопределенных констант и функций. Константы представляют собой определенные числа. Одно из таких чисел — значение числа пи (приблизительно 3,14159...). Эта константа называется **Math.PI** и демонстрируется в следующем примере.  
  
```JavaScript  
var radius = 5;  
var circleArea = Math.PI * radius * radius;  
```  
  
 Одной из встроенных функций объекта **Math** является метод возведения в степень (`Math.pow`), возводящий число в указанную степень. В следующем примере число пи и возведение в степень используются для вычисления объема сферы.  
  
```JavaScript  
var volume = (4/3)*(Math.PI*Math.pow(radius,3));  
```  
  
## <a name="date-object"></a>Объект Date  
 Объект `Date` может использоваться для представления произвольных даты и времени, получения текущей системной даты и вычисления разницы между датами. У него есть несколько свойств и методов, все из которых являются предопределенными. Как правило, объект `Date` предоставляет день недели, месяц, день и год, а также время в часах, минутах и секундах. Эти данные опираются на число миллисекунд, прошедших с 00:00:00.000 1 января 1970 г. GMT (среднее время по Гринвичу; предпочтительным является термин UTC, или универсальное скоординированное время, соответствующее стандартному мировому времени). [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] позволяет обрабатывать даты в диапазоне от 250 000 года до нашей эры до 255 000 года нашей эры.  
  
 Чтобы создать объект `Date`, используйте оператор **new**, как показано в следующем примере.  
  
```JavaScript  
var toDay = new Date();    
var thisYear = toDay.getFullYear();  
var thisMonth = theMonths[toDay.getMonth()];  
var thisDay = thisMonth  + " " + toDay.getDate() + ", " + thisYear;  
```  
  
## <a name="number-object"></a>Объект Number  
 Наряду со специальными числовыми константами (например, `PI`), доступными в объекте **Math**, в [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] можно использовать и некоторые другие константы, доступные через объект **Number**.  
  
|Константа|Описание|  
|--------------|-----------------|  
|Number.MAX_VALUE|Наибольшее возможное число, которое равно приблизительно 1,79E+308; может быть положительным или отрицательным (значение может несколько изменяться в зависимости от используемой системы).|  
|Number.MIN_VALUE|Наименьшее возможное число, которое равно приблизительно 5,00E-324; может быть положительным или отрицательным (значение может несколько изменяться в зависимости от используемой системы).|  
|Number.NaN|Особое нечисловое значение, "не число".|  
|Number.POSITIVE_INFINITY|В это значение автоматически преобразуется любое значение, превышающее наибольшее возможное положительное число (Number.MAX_VALUE); представляется как infinity.|  
|Number.NEGATIVE_INFINITY|В это значение автоматически преобразуется любое значение, более отрицательное, чем наибольшее возможное отрицательное число (-Number.MAX_VALUE); представляется как -infinity.|  
  
 **Number.NaN** — это особая константа, которая определяется как "не число". Попытка выполнить синтаксический анализ строки, которую невозможно проанализировать как число, возвращает значение **Number.NaN**. При сравнении значение `NaN` оказывается неравным ни какому-либо числу, ни самому себе. Для проверки на наличие результата `NaN` не следует выполнять сравнение со значением **Number.NaN**; используйте вместо этого функцию **isNaN()**.  
  
## <a name="json-object"></a>Объект JSON  
 JSON представляет собой облегченный формат обмена данными на основе подмножества нотации объектного литерала в языке JavaScript.  
  
 Объект JSON предоставляет две функции для преобразования в формат текста JSON и из него. Функция [JSON.stringify](../javascript/reference/json-stringify-function-javascript.md) сериализует объекты и массивы в текст JSON. Функция [JSON.parse](../javascript/reference/json-parse-function-javascript.md) десериализует текст JSON для создания объектов в памяти. Дополнительные сведения см. в статье [Введение в нотацию объектов JavaScript (JSON) в JavaScript и .NET](http://go.microsoft.com/fwlink/?LinkId=124098).  
  
## <a name="see-also"></a>См. также  
 [Объекты JavaScript](../javascript/reference/javascript-objects.md)