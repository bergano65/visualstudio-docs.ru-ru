---
title: "Метод every (Array) (JavaScript) | Microsoft Docs"
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
  - "массивы [JavaScript], every - метод"
  - "every - метод"
ms.assetid: dc4ee2f8-fb9e-4c9f-af5a-fe836e40ddd1
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Метод every (Array) (JavaScript)
Определяет, все ли члены массива удовлетворяют указанному тесту.  
  
## Синтаксис  
  
```  
  
array1.every(callbackfn[, thisArg])  
```  
  
#### Параметры  
  
|Параметр|Определение|  
|--------------|-----------------|  
|`array1`|Обязательный.  Объект массива.|  
|`callbackfn`|Обязательный.  Функция, принимающая до трех аргументов.  Метод `every` вызывает функцию `callbackfn` для каждого элемента в массиве `array1`, пока функция `callbackfn` не вернет значение `false` или не будет достигнут конец массива.|  
|`thisArg`|Необязательный.  Объект, на который может ссылаться ключевое слово `this` в функции `callbackfn`.  Если аргумент `thisArg` опущен, в качестве значения `this` используется `undefined`.|  
  
## Возвращаемое значение  
 Значение `true`, если функция `callbackfn` возвращает значение `true` для всех элементов массива; в противном случае — значение `false`.  Если массив не содержит элементов, метод `every` возвращает значение `true`.  
  
## Исключения  
 Если аргумент `callbackfn` не является объектом функции, вызывается исключение `TypeError`.  
  
## Заметки  
 Метод `every` вызывает функцию `callbackfn` по одному разу для каждого элемента массива \(в порядке возрастания индекса\), пока функция `callbackfn` не вернет значение `false`.  Если элемент, для которого функция `callbackfn` возвращает значение `false`, найден, метод `every` немедленно возвращает значение `false`.  В противном случае метод `every` возвращает значение `true`.  
  
 Функция обратного вызова не вызывается для отсутствующих элементов массива.  
  
 Помимо объектов массива, метод `every` может использоваться любым объектом, имеющим свойство `length` и обладающим численно проиндексированными именами свойств.  
  
> [!NOTE]
>  [Метод some \(Array\)](../../javascript/reference/some-method-array-javascript.md) позволяет проверить, возвращает ли функция обратного вызова значение `true` для какого\-либо из элементов массива.  
  
## Синтаксис функции обратного вызова  
 Синтаксис функции обратного вызова таков:  
  
 `function callbackfn(value, index, array1)`  
  
 Можно объявить функцию обратного вызова, используя до трех параметров.  
  
 В приведенной ниже таблице перечислены параметры функции обратного вызова.  
  
|Параметр обратного вызова|Определение|  
|-------------------------------|-----------------|  
|`value`|Значение элемента массива.|  
|`index`|Числовой индекс элемента массива.|  
|`array1`|Объект массива, содержащий требуемый элемент.|  
  
## Изменение объекта массива  
 Объект массива может изменяться функцией обратного вызова.  
  
 В следующей таблице описаны результаты изменения объекта массива после запуска метода `every`.  
  
|Условие после запуска метода `every`|Элемент передается функции обратного вызова?|  
|------------------------------------------|--------------------------------------------------|  
|Элемент добавлен за пределами первоначальной длины массива.|Нет.|  
|Элемент добавлен для заполнения отсутствующего элемента массива.|Да, если этот индекс еще не был передан функции обратного вызова.|  
|Элемент изменен.|Да, если этот элемент еще не был передан функции обратного вызова.|  
|Элемент удален из массива.|Нет, если этот элемент не был уже передан функции обратного вызова.|  
  
## Пример  
 В следующем примере показано использование метода `every`.  
  
```javascript  
// Define the callback function.  
function CheckIfEven(value, index, ar) {  
    document.write(value + " ");  
  
    if (value % 2 == 0)  
        return true;  
    else  
        return false;  
}  
  
// Create an array.  
var numbers = [2, 4, 5, 6, 8];  
  
// Check whether the callback function returns true for all of the  
// array values.  
if (numbers.every(CheckIfEven))  
    document.write("All are even.");  
else  
    document.write("Some are not even.");  
  
// Output:  
// 2 4 5 Some are not even.  
```  
  
## Пример  
 В следующем примере показано использование аргумента `thisArg`, задающего объект, на который может ссылаться ключевое слово `this`.  
  
```javascript  
// Create a function that returns true if the value is  
// numeric and within range.  
var checkNumericRange = function(value) {  
    if (typeof value !== 'number')  
        return false;  
    else   
        return value >= this.minimum && value <= this.maximum;  
}  
  
// Create an array of numbers.  
var numbers = [10, 15, 19];  
  
// Check whether the callback function returns true for  
// all of the array values.  
// The obj argument enables use of the this value  
// within the callback function.  
  
var obj = { minimum: 10, maximum: 20 }  
  
if (numbers.every(checkNumericRange, obj))  
    document.write ("All are within range.");  
else  
    document.write ("Some are not within range.");  
  
// Output:  
//   All are within range.  
  
```  
  
## Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## См. также  
 [Метод some \(Array\)](../../javascript/reference/some-method-array-javascript.md)   
 [Метод filter \(Array\)](../../javascript/reference/filter-method-array-javascript.md)   
 [Объект Array](../../javascript/reference/array-object-javascript.md)   
 [Использование массивов](../../javascript/advanced/using-arrays-javascript.md)