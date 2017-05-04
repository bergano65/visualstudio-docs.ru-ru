---
title: "Функция JSON.parse (JavaScript) | Microsoft Docs"
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
  - "JSON.parse"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JSON.parse - метод"
  - "метод синтаксического анализа JSON"
ms.assetid: 20f00d31-5ab5-4c3c-ab49-2534fc39a9b4
caps.latest.revision: 41
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 41
---
# Функция JSON.parse (JavaScript)
Преобразует строку нотации объектов JavaScript \(JSON\) в объект.  
  
## Синтаксис  
  
```  
JSON.parse(text [, reviver])  
```  
  
## Параметры  
 `text`  
 Обязательный. Допустимая строка JSON.  
  
 `reviver`  
 Необязательный. Функция, преобразующая результаты. Эта функция вызывается для каждого члена объекта. Если член содержит вложенные объекты, они преобразуются до преобразования родительского объекта. Для каждого члена происходит одно из следующих событий.  
  
-   Если параметр `reviver` возвращает допустимое значение, значение члена заменяется преобразованным значением.  
  
-   Если параметр `reviver` возвращает то же значение, что он получил, значение члена не изменяется.  
  
-   Если `reviver` возвращает `null` или `undefined`, член удаляется.  
  
## Возвращаемое значение  
 Объект или массив.  
  
## Исключения  
 Если эта функция приводит к появлению ошибки синтаксического анализатора [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] \(например, "SCRIPT1014. Недопустимый символ"\), введенный текст не соответствует синтаксису JSON. Чтобы устранить эту ошибку, выполните одно из следующих действий.  
  
-   Измените аргумент `text`, чтобы он соответствовал синтаксису JSON. Дополнительные сведения см. в [описании нотации синтаксиса BNF](http://go.microsoft.com/fwlink/?LinkId=125203) объектов JSON.  
  
     Например, если отклик имеет формат JSONP вместо чистого JSON, попробуйте использовать этот код в объекте отклика.  
  
    ```javascript  
    var fixedResponse = response.responseText.replace(/\\'/g, "'");  
    var jsonObj = JSON.parse(fixedResponse);  
    ```  
  
-   Убедитесь, что аргумент `text` был сериализован реализацией, совместимой с JSON, например `JSON.stringify`.  
  
-   Запустите аргумент `text` в проверяющем элементе управления JSON, например [JSLint](http://www.jslint.com/), для идентификации синтаксических ошибок.  
  
## Пример  
 В следующем примере используется `JSON.parse` для преобразования строки JSON в объект.  
  
```javascript  
var jsontext = '{"firstname":"Jesper","surname":"Aaberg","phone":["555-0100","555-0120"]}';  
var contact = JSON.parse(jsontext);  
document.write(contact.surname + ", " + contact.firstname);  
document.write(contact.phone[1]);  
// Output:  
// Aaberg, Jesper  
// 555-0100  
```  
  
## Пример  
 В следующем примере показано преобразование массива в строку JSON с помощью `JSON.stringify`, а затем преобразование этой строки обратно в массив с помощью `JSON.parse`.  
  
```javascript  
var arr = ["a", "b", "c"];  
var str = JSON.stringify(arr);  
document.write(str);  
document.write ("<br/>");  
  
var newArr = JSON.parse(str);  
  
while (newArr.length > 0) {  
    document.write(newArr.pop() + "<br/>");  
}  
  
// Output:  
// ["a","b","c"]  
// c  
// b  
// a  
```  
  
## Пример  
 Функция `reviver` часто используется для преобразования представления JSON строк дат Международной организации по стандартизации \(ISO\) в объекты `Date` в формате универсального времени \(UTC\). В этом примере используется `JSON.parse` для десериализации строки даты в формате ISO. Функция `dateReviver` возвращает объекты `Date` для членов, отформатированных как строки даты ISO.  
  
```javascript  
var jsontext = '{ "hiredate": "2008-01-01T12:00:00Z", "birthdate": "2008-12-25T12:00:00Z" }';  
var dates = JSON.parse(jsontext, dateReviver);  
document.write(dates.birthdate.toUTCString());  
  
function dateReviver(key, value) {  
    var a;  
    if (typeof value === 'string') {  
        a = /^(\d{4})-(\d{2})-(\d{2})T(\d{2}):(\d{2}):(\d{2}(?:\.\d*)?)Z$/.exec(value);  
        if (a) {  
            return new Date(Date.UTC(+a[1], +a[2] - 1, +a[3], +a[4],  
                            +a[5], +a[6]));  
        }  
    }  
    return value;  
};  
  
// Output:  
// Thu, 25 Dec 2008 12:00:00 UTC  
  
```  
  
## Требования  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## См. также  
 [Функция JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md)   
 [Метод toJSON \(Date\)](../../javascript/reference/tojson-method-date-javascript.md)   
 [Пример приложения шаблона концентратора \(Магазин Windows\)](http://code.msdn.microsoft.com/Hub-template-sample-with-4b70002d)