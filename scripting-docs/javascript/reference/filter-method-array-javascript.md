---
title: "Метод filter (Array) (JavaScript) | Microsoft Docs"
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
  - "массивы [JavaScript], filter - метод"
  - "filter - метод [JavaScript]"
ms.assetid: 1d260370-9e6e-43fc-870f-2d35850db7ee
caps.latest.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 32
---
# Метод filter (Array) (JavaScript)
Возвращает элементы массива, удовлетворяющие условию, указанному в функции обратного вызова.  
  
## Синтаксис  
  
```  
  
array1.filter(callbackfn[, thisArg])  
```  
  
#### Параметры  
  
|Параметр|Определение|  
|--------------|-----------------|  
|`array1`|Обязательный.  Объект массива.|  
|`callbackfn`|Обязательный.  Функция, принимающая до трех аргументов.  Метод `filter` вызывает функцию `callbackfn` по одному разу для каждого элемента массива.|  
|`thisArg`|Необязательный.  Объект, на который может ссылаться ключевое слово `this` в функции `callbackfn`.  Если аргумент `thisArg` опущен, в качестве значения `this` используется `undefined`.|  
  
## Возвращаемое значение  
 Новый массив, содержащий все значения, для которых функция обратного вызова возвращает значение `true`.  Если функция обратного вызова возвращает значение `false` для всех элементов `array1`, длина нового массива равна 0.  
  
## Исключения  
 Если аргумент `callbackfn` не является объектом функции, вызывается исключение `TypeError`.  
  
## Заметки  
 Метод `filter` вызывает функцию `callbackfn` по одному разу для каждого элемента массива в порядке возрастания индекса.  Функция обратного вызова не вызывается для отсутствующих элементов массива.  
  
 Помимо объектов массива, метод `filter` может использоваться любым объектом, имеющим свойство `length` и обладающим численно проиндексированными именами свойств.  
  
## Синтаксис функции обратного вызова  
 Синтаксис функции обратного вызова таков:  
  
 `function callbackfn(value, index, array1)`  
  
 Можно объявить функцию обратного вызова, используя до трех параметров.  
  
 В приведенной ниже таблице перечислены параметры функции обратного вызова.  
  
|Аргумент обратного вызова|Определение|  
|-------------------------------|-----------------|  
|`value`|Значение элемента массива.|  
|`index`|Числовой индекс элемента массива.|  
|`array1`|Объект массива, содержащий требуемый элемент.|  
  
## Изменение объекта массива  
 Сам метод `filter` не изменяет исходный массив, но функция обратного вызова может изменять его.  В следующей таблице описаны результаты изменения объекта массива после запуска метода `filter`.  
  
|Условие после запуска метода `filter`|Элемент передается функции обратного вызова?|  
|-------------------------------------------|--------------------------------------------------|  
|Элемент добавлен за пределами первоначальной длины массива.|Нет.|  
|Элемент добавлен для заполнения отсутствующего элемента массива.|Да, если этот индекс еще не был передан функции обратного вызова.|  
|Элемент изменен.|Да, если этот элемент еще не был передан функции обратного вызова.|  
|Элемент удален из массива.|Нет, если этот элемент не был уже передан функции обратного вызова.|  
  
## Пример  
 В следующем примере показано использование метода `filter`.  
  
```javascript  
// Define a callback function.  
function CheckIfPrime(value, index, ar) {  
    high = Math.floor(Math.sqrt(value)) + 1;  
  
    for (var div = 2; div <= high; div++) {  
        if (value % div == 0) {  
            return false;  
        }  
    }   
    return true;  
}  
  
// Create the original array.  
var numbers = [31, 33, 35, 37, 39, 41, 43, 45, 47, 49, 51, 53];  
  
// Get the prime numbers that are in the original array.   
var primes = numbers.filter(CheckIfPrime);  
  
document.write(primes);  
// Output: 31,37,41,43,47,53  
```  
  
## Пример  
 В следующем примере аргумент `callbackfn` включает код функции обратного вызова.  
  
```javascript  
// Create the original array.  
var arr = [5, "element", 10, "the", true];  
  
// Create an array that contains the string  
// values that are in the original array.  
var result = arr.filter(  
    function (value) {  
        return (typeof value === 'string');  
    }  
);  
  
document.write(result);  
// Output: element, the  
```  
  
## Пример  
 В следующем примере выводятся имена свойств в объекте DOM `window`, начинающиеся с букв "css".  
  
```javascript  
var filteredNames = Object.getOwnPropertyNames(window).filter(IsC);  
  
    for (i in filteredNames)  
        document.write(filteredNames[i] + "<br/>");  
  
// Check whether the string starts with "css".  
function IsC(value) {  
    var firstChar = value.substr(0, 3);  
    if (firstChar.toLowerCase() == "css")  
        return true;  
    else  
        return false;  
    }  
  
// Output:  
// CSSRule  
// CSSFontFaceRule  
// CSSImportRule  
// CSSMediaRule  
// CSSNamespaceRule  
// CSSPageRule  
// CSSRuleList  
// CSSStyleDeclaration  
// CSSStyleRule  
// CSSStyleSheet  
  
```  
  
## Пример  
 В следующем примере показано использование аргумента `thisArg`, задающего объект, на который может ссылаться ключевое слово `this`.  
  
```javascript  
var checkNumericRange = function(value) {  
    if (typeof value !== 'number')  
        return false;  
    else   
        return value >= this.minimum && value <= this.maximum;  
}  
  
var numbers = [6, 12, "15", 16, "the", -12];  
  
// The obj argument enables use of the this value  
// within the callback function.  
var obj = { minimum: 10, maximum: 20 }  
  
var result = numbers.filter(checkNumericRange, obj);  
  
document.write(result);  
// Output: 12,16  
  
```  
  
## Пример  
 Метод `filter` можно применить к строке, а не массиву.  Следующий пример показывает, как это сделать.  
  
```javascript  
// Define a callback function that returns true  
// if the current array element follows a space  
// or is the first character.  
function CheckValue(value, index, ar) {  
    if (index == 0)  
        return true;  
    else  
        return ar[index - 1] === " ";  
}  
  
// Create a string.  
var sentence = "The quick brown fox jumps over the lazy dog.";   
  
// Create an array that contains all characters that follow a space.  
var subset = [].filter.call(sentence, CheckValue);   
  
// You can use this alternative syntax.  
//var subset = Array.prototype.filter.call(sentence, CheckValue);  
  
document.write(subset);  
// Output: T,q,b,f,j,o,t,l,d  
  
```  
  
## Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## См. также  
 [Объект Array](../../javascript/reference/array-object-javascript.md)   
 [Использование массивов](../../javascript/advanced/using-arrays-javascript.md)   
 [Метод map \(Array\)](../../javascript/reference/map-method-array-javascript.md)   
 [Метод forEach \(Array\)](../../javascript/reference/foreach-method-array-javascript.md)