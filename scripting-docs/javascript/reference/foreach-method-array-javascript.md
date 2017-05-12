---
title: "Метод forEach (Array) (JavaScript) | Microsoft Docs"
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
  - "массивы [JavaScript], forEach - метод"
  - "функция обратного вызова, forEach - метод [JavaScript]"
  - "forEach - метод [JavaScript]"
ms.assetid: bd188034-a62b-4cbd-99c8-46d70dd6823d
caps.latest.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 28
---
# Метод forEach (Array) (JavaScript)
Выполняет указанное действие для каждого элемента массива.  
  
## Синтаксис  
  
```  
  
array1.forEach(callbackfn[, thisArg])  
```  
  
#### Параметры  
  
|Параметр|Определение|  
|--------------|-----------------|  
|`array1`|Обязательный.  Объект массива.|  
|`callbackfn`|Обязательный.  Функция, которая принимает до 3 аргументов.  Метод `forEach` вызывает функцию `callbackfn` по одному разу для каждого элемента массива.|  
|`thisArg`|Необязательный.  Объект, на который может ссылаться ключевое слово `this` в функции `callbackfn`.  Если параметр `thisArg` опущен, в качестве значения `this` используется `undefined`.|  
  
## Исключения  
 Если аргумент `callbackfn` не является объектом функции, вызывается исключение `TypeError`.  
  
## Заметки  
 Метод `forEach` вызывает функцию `callbackfn` по одному разу для каждого элемента массива в порядке возрастания индекса.  Функция обратного вызова не вызывается для отсутствующих элементов массива.  
  
 Помимо объектов массива, метод `forEach` может использоваться любым объектом, имеющим свойство `length` и обладающим численно проиндексированными именами свойств.  
  
## Синтаксис функции обратного вызова  
 Синтаксис функции обратного вызова выглядит следующим образом:  
  
 `function callbackfn(value, index, array1)`  
  
 При объявлении функции обратного вызова можно использовать до трех параметров.  
  
 Функция обратного вызова имеет следующие параметры.  
  
|Аргумент обратного вызова|Определение|  
|-------------------------------|-----------------|  
|`value`|Значение элемента массива.|  
|`index`|Числовой индекс элемента массива.|  
|`array1`|Объект массива, содержащий требуемый элемент.|  
  
## Изменение объекта массива  
 Сам метод `forEach` не изменяет исходный массив, но функция обратного вызова может изменять его.  В следующей таблице описаны результаты изменения объекта массива после запуска метода `forEach`.  
  
|Условие после запуска метода `forEach`|Элемент передается функции обратного вызова?|  
|--------------------------------------------|--------------------------------------------------|  
|Элемент добавлен за пределами первоначальной длины массива.|Нет.|  
|Элемент добавлен для заполнения отсутствующего элемента массива.|Да, если этот индекс еще не был передан функции обратного вызова.|  
|Элемент изменен.|Да, если этот элемент еще не был передан функции обратного вызова.|  
|Элемент удален из массива.|Нет, если этот элемент не был уже передан функции обратного вызова.|  
  
## Пример  
 В следующем примере показано использование метода `forEach`.  
  
```javascript  
// Define the callback function.  
function ShowResults(value, index, ar) {  
    document.write("value: " + value);  
    document.write(" index: " + index);  
    document.write("<br />");  
}  
  
// Create an array.  
var letters = ['ab', 'cd', 'ef'];  
  
// Call the ShowResults callback function for each  
// array element.  
letters.forEach(ShowResults);  
  
// Output:  
//  value: ab index: 0   
//  value: cd index: 1   
//  value: ef index: 2   
```  
  
## Пример  
 В следующем примере аргумент `callbackfn` включает код функции обратного вызова.  
  
```javascript  
// Create an array.  
var numbers = [10, 11, 12];  
  
// Call the addNumber callback function for each array element.  
var sum = 0;  
numbers.forEach(  
    function addNumber(value) { sum += value; }  
);  
  
document.write(sum);  
// Output: 33  
  
```  
  
## Пример  
 В следующем примере показано использование аргумента `thisArg`, указывающего объект, на который можно ссылаться с помощью ключевого слова `this`.  
  
```javascript  
// Define the object that contains the callback function.  
var obj = {  
    showResults: function(value, index) {  
        // Call calcSquare by using the this value.  
        var squared = this.calcSquare(value);  
  
        document.write("value: " + value);  
        document.write(" index: " + index);  
        document.write(" squared: " + squared);  
        document.write("<br />");  
    },  
    calcSquare: function(x) { return x * x }  
};  
  
// Define an array.  
var numbers = [5, 6];  
  
// Call the showResults callback function for each array element.  
// The obj is the this value within the   
// callback function.  
numbers.forEach(obj.showResults, obj);  
  
// Embed the callback function in the forEach statement.  
// The obj argument is the this value within the obj object.  
// The output is the same as for the previous statement.  
numbers.forEach(function(value, index) { this.showResults(value, index) }, obj);  
  
// Output:  
//  value: 5 index: 0 squared: 25  
//  value: 6 index: 1 squared: 36  
//  value: 5 index: 0 squared: 25  
//  value: 6 index: 1 squared: 36  
```  
  
## Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## См. также  
 [Метод filter \(Array\)](../../javascript/reference/filter-method-array-javascript.md)   
 [Метод map \(Array\)](../../javascript/reference/map-method-array-javascript.md)   
 [Метод some \(Array\)](../../javascript/reference/some-method-array-javascript.md)   
 [Объект Array](../../javascript/reference/array-object-javascript.md)   
 [Использование массивов](../../javascript/advanced/using-arrays-javascript.md)   
 [Пример приложения Hilo на JavaScript \(Магазин Windows\)](http://hilojs.codeplex.com/SourceControl/latest)