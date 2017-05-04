---
title: "Функция JSON.stringify (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "stringify - метод"
ms.assetid: 0fafaf3b-c29b-46dc-b65b-ca223064a1d0
caps.latest.revision: 40
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 40
---
# Функция JSON.stringify (JavaScript)
Преобразует значение [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] в строку JSON \(нотация объектов JavaScript\).  
  
## Синтаксис  
  
```  
  
JSON.stringify(  
value [, replacer] [, space])  
```  
  
## Параметры  
 `value`  
 Обязательный.  Преобразуемое значение [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], обычно объект или массив.  
  
 `replacer`  
 Необязательный.  Функция или массив, используемые для преобразования результатов.  
  
 Если `replacer` представляет собой функцию, метод `JSON.stringify` вызывает эту функцию, передавая ей ключ и значение каждого члена.  Возвращаемое значение используется вместо исходного значения.  Если функция возвращает значение `undefined`, член исключается.  Ключ для корневого объекта — это пустая строка: "".  
  
 Если `replacer` представляет собой массив, преобразуются только члены со значениями ключа, присутствующими в массиве.  Порядок преобразования членов соответствует порядку ключей в массиве.  Массив в аргументе `replacer` игнорируется, если аргумент `value` также является массивом.  
  
 `space`  
 Необязательный.  Добавляет отступы, пробелы и символы разрыва строки в текст JSON возвращаемого значения, чтобы сделать его более удобным для чтения.  
  
 Если аргумент `space` опущен, текст возвращаемого значения создается без дополнительных пробелов.  
  
 Если `space` представляет собой число, в текст возвращаемого значения вставляются отступы на указанное число пробелов на каждом уровне.  Если `space` больше 10, отступ текста составляет 10 пробелов.  
  
 Если `space` представляет собой непустую строку, например '\\t', в текст возвращаемого значения в качестве отступа на каждом уровне вставляются символы этой строки.  
  
 Если `space` представляет собой строку длиннее 10 символов, используются первые 10 символов.  
  
## Возвращаемое значение  
 Строка, содержащая текст JSON.  
  
## Исключения  
  
|Исключение|Условие|  
|----------------|-------------|  
|[Недопустимый аргумент замены](../../javascript/misc/invalid-replacer-argument.md)|Аргумент `replacer` не является функцией или массивом.|  
|[Циклические ссылки не поддерживаются в аргументах значений](../../javascript/misc/circular-reference-in-value-argument-not-supported.md)|Аргумент `value` содержит циклическую ссылку.|  
  
## Заметки  
 Если `value` содержит метод `toJSON`, функция `JSON.stringify` использует возвращаемое значение этого метода.  Если метод `toJSON` возвращает значение `undefined`, член не преобразуется.  Это позволяет объекту определить собственное представление JSON.  
  
 Значения, которые не имеют представления JSON, такие как `undefined`, не будут преобразованы.  В объектах они будут удалены.  В массивах они будут заменены значением NULL.  
  
 Строковые значения начинаются и заканчиваются кавычкой.  Все символы Юникода могут быть заключены в кавычки, за исключением символов, которые должны предваряться escape\-символом \(обратной косой чертой\).  Предваряться обратной косой чертой должны следующие символы:  
  
-   кавычка \("\);  
  
-   обратная косая черта \(\\\);  
  
-   BACKSPACE \(b\);  
  
-   перевод страницы \(f\);  
  
-   новая строка \(\\n\);  
  
-   возврат каретки \(r\);  
  
-   горизонтальная табуляция \(t\);  
  
-   четыре шестнадцатеричные цифры \(uhhhh\).  
  
## Порядок выполнения  
 Если в процессе сериализации для аргумента `value` существует метод `toJSON`, метод `JSON.stringify` сначала вызывает метод `toJSON`.  Если он не существует, используется исходное значение.  Далее, если предоставлен аргумент `replacer`, значение \(исходное значение или возвращаемое значение метода `toJSON`\) заменяется возвращаемым значением аргумента `replacer`.  Наконец, к значению добавляются пробелы в соответствии с необязательным аргументом `space` для получения конечного текста JSON.  
  
## Пример  
 В этом примере метод `JSON.stringify` преобразует объект `contact` в текст JSON.  Массив `memberfilter` задан так, что преобразуются только члены `surname` и `phone`.  Член `firstname` пропускается.  
  
```javascript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Array();  
memberfilter[0] = "surname";  
memberfilter[1] = "phone";  
var jsonText = JSON.stringify(contact, memberfilter, "\t");  
document.write(jsonText);  
// Output:   
// { "surname": "Aaberg", "phone": [ "555-0100", "555-0120" ] }  
```  
  
## Пример  
 В этом примере используется метод `JSON.stringify` с массивом.  Функция `replaceToUpper` преобразует каждую строку массива в верхний регистр.  
  
```javascript  
var continents = new Array();  
continents[0] = "Europe";  
continents[1] = "Asia";  
continents[2] = "Australia";  
continents[3] = "Antarctica";  
continents[4] = "North America";  
continents[5] = "South America";  
continents[6] = "Africa";  
  
var jsonText = JSON.stringify(continents, replaceToUpper);  
  
function replaceToUpper(key, value) {  
    return value.toString().toUpperCase();  
}  
  
//Output:  
// "EUROPE,ASIA,AUSTRALIA,ANTARCTICA,NORTH AMERICA,SOUTH AMERICA,AFRICA"  
  
```  
  
## Пример  
 В этом примере метод `toJSON` преобразует строковые значения в верхний регистр.  
  
```javascript  
var contact = new Object();   
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
contact.toJSON = function(key)  
 {  
    var replacement = new Object();  
    for (var val in this)  
    {  
        if (typeof (this[val]) === 'string')  
            replacement[val] = this[val].toUpperCase();  
        else  
            replacement[val] = this[val]  
    }  
    return replacement;  
};  
  
var jsonText = JSON.stringify(contact);  
document.write(jsonText);  
  
// Output:  
{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}  
  
'{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}'  
*/  
```  
  
## Требования  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## См. также  
 [Функция JSON.parse](../../javascript/reference/json-parse-function-javascript.md)   
 [Метод toJSON \(Date\)](../../javascript/reference/tojson-method-date-javascript.md)   
 [Пример средства чтения веб\-каналов \(Магазин Windows\)](http://code.msdn.microsoft.com/Feed-reader-sample-99d68cf8)