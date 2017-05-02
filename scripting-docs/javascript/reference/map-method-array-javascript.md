---
title: "Метод map (Array) (JavaScript) | Microsoft Docs"
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
  - "массивы [JavaScript], map - метод"
  - "map - метод [JavaScript]"
ms.assetid: 500dc4f8-d73d-4a28-a5b8-c9bd5674ea36
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Метод map (Array) (JavaScript)
Вызывает заданную функцию обратного вызова для каждого элемента массива и возвращает массив, содержащий результаты.  
  
## Синтаксис  
  
```  
  
array1.map(callbackfn[, thisArg])  
```  
  
#### Параметры  
  
|Параметр|Определение|  
|--------------|-----------------|  
|`array1`|Обязательный.  Объект массива.|  
|`callbackfn`|Обязательный.  Функция, которая принимает до 3 аргументов.  Метод `map` вызывает функцию `callbackfn` по одному разу для каждого элемента массива.|  
|`thisArg`|Необязательный.  Объект, на который может ссылаться ключевое слово `this` в функции `callbackfn`.  Если параметр `thisArg` опущен, в качестве значения `this` используется `undefined`.|  
  
## Возвращаемое значение  
 Новый массив, в котором каждый элемент — возвращаемое значение функции обратного вызова для связанного исходного элемента массива.  
  
## Исключения  
 Если аргумент `callbackfn` не является объектом функции, вызывается исключение `TypeError`.  
  
## Заметки  
 Метод `map` вызывает функцию `callbackfn` по одному разу для каждого элемента массива в порядке возрастания индекса.  Функция обратного вызова не вызывается для отсутствующих элементов массива.  
  
 Помимо объектов массива, метод `map` может использоваться любым объектом, имеющим свойство `length` и обладающим численно проиндексированными именами свойств.  
  
## Синтаксис функции обратного вызова  
 Синтаксис функции обратного вызова выглядит следующим образом:  
  
 `function callbackfn(value, index, array1)`  
  
 При объявлении функции обратного вызова можно использовать до трех параметров.  
  
 В следующей таблице перечислены параметры функции обратного вызова.  
  
|Аргумент обратного вызова|Определение|  
|-------------------------------|-----------------|  
|`value`|Значение элемента массива.|  
|`index`|Числовой индекс элемента массива.|  
|`array1`|Объект массива, содержащий требуемый элемент.|  
  
## Изменение объекта массива  
 Объект массива может изменяться функцией обратного вызова.  
  
 В следующей таблице описаны результаты изменения объекта массива после запуска метода `map`.  
  
|Условие после запуска метода `map`|Элемент передается функции обратного вызова?|  
|----------------------------------------|--------------------------------------------------|  
|Элемент добавлен за пределами первоначальной длины массива.|Нет.|  
|Элемент добавлен для заполнения отсутствующего элемента массива.|Да, если этот индекс еще не был передан функции обратного вызова.|  
|Элемент изменен.|Да, если этот элемент еще не был передан функции обратного вызова.|  
|Элемент удален из массива.|Нет, если этот элемент не был уже передан функции обратного вызова.|  
  
## Пример  
 В следующем примере показано использование метода `map`.  
  
```javascript  
// Define the callback function.  
function AreaOfCircle(radius) {  
    var area = Math.PI * (radius * radius);  
    return area.toFixed(0);  
}  
  
// Create an array.  
var radii = [10, 20, 30];  
  
// Get the areas from the radii.  
var areas = radii.map(AreaOfCircle);  
  
document.write(areas);  
  
// Output:  
// 314,1257,2827  
```  
  
## Пример  
 В следующем примере показано использование аргумента `thisArg`, задающего объект, на который может ссылаться ключевое слово `this`.  
  
```javascript  
// Define an object that contains a divisor property and  
// a remainder function.  
var obj = {  
    divisor: 10,  
    remainder: function (value) {  
        return value % this.divisor;  
    }  
}  
  
// Create an array.  
var numbers = [6, 12, 25, 30];  
  
// Get the remainders.  
// The obj argument specifies the this value in the callback function.  
var result = numbers.map(obj.remainder, obj);  
document.write(result);  
  
// Output:  
// 6,2,5,0  
```  
  
## Пример  
 В следующем примере встроенный метод [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] используется как функция обратного вызова.  
  
```javascript  
// Apply Math.sqrt(value) to each element in an array.  
var numbers = [9, 16];  
var result = numbers.map(Math.sqrt);  
  
document.write(result);  
// Output: 3,4  
```  
  
## Пример  
 Метод `map` может быть применен к строке.  Это показано в следующем примере.  
  
```javascript  
// Define the callback function.  
function threeChars(value, index, str) {  
    // Create a string that contains the previous, current,  
    // and next character.  
    return str.substring(index - 1, index + 2);  
}  
  
// Create a string.  
var word = "Thursday";  
  
// Apply the map method to the string.  
// Each array element in the result contains a string that  
// has the previous, current, and next character.  
// The commented out statement shows an alternative syntax.  
var result = [].map.call(word, threeChars);  
// var result = Array.prototype.map.call(word, threeChars);  
  
document.write(result);  
  
// Output:  
// Th,Thu,hur,urs,rsd,sda,day,ay  
  
```  
  
## Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## См. также  
 [Методы JavaScript](../../javascript/reference/javascript-methods.md)   
 [Объект Array](../../javascript/reference/array-object-javascript.md)   
 [Использование массивов](../../javascript/advanced/using-arrays-javascript.md)   
 [Метод filter \(Array\)](../../javascript/reference/filter-method-array-javascript.md)   
 [Метод forEach \(Array\)](../../javascript/reference/foreach-method-array-javascript.md)   
 [Пример приложения Hilo на JavaScript \(Магазин Windows\)](http://hilojs.codeplex.com/SourceControl/latest)