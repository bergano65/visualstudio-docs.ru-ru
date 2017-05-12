---
title: "Метод reduce (Array) (JavaScript) | Microsoft Docs"
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
  - "массивы [JavaScript], reduce - метод"
  - "функция обратного вызова, reduce - метод [JavaScript]"
  - "reduce - метод [JavaScript]"
ms.assetid: 48d069e0-e083-494f-86d5-d459d2377dc5
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# Метод reduce (Array) (JavaScript)
Вызывает заданную функцию обратного вызова для всех элементов в массиве.  Возвращаемое значение функции обратного вызова представляет собой накопленный результат и предоставляется как аргумент в следующем вызове функции обратного вызова.  
  
## Синтаксис  
  
```  
  
array1.reduce(callbackfn[, initialValue])  
```  
  
#### Параметры  
  
|Параметр|Определение|  
|--------------|-----------------|  
|`array1`|Обязательный.  Объект массива.|  
|`callbackfn`|Обязательный.  Функция, которая принимает до четырех аргументов.  Метод `reduce` вызывает функцию `callbackfn` по одному разу для каждого элемента массива.|  
|`initialValue`|Необязательный.  Если значение `initialValue` указано, оно используется в качестве начального значения, с которого начинается накопление.  При первом вызове функции `callbackfn` в качестве аргумента вместо значения из массива предоставляется это значение.|  
  
## Возвращаемое значение  
 Накопленный результат последнего вызова функции обратного вызова.  
  
## Исключения  
 Исключение `TypeError` возникает, если выполняется одно из следующих условий.  
  
-   Аргумент `callbackfn` не является объектом функции.  
  
-   Массив не содержит элементов и `initialValue` не предоставлено.  
  
## Заметки  
 Если значение `initialValue` предоставлено, метод `reduce` вызывает функцию `callbackfn` по одному разу для каждого элемента массива в порядке возрастания индекса.  Если значение `initialValue` не предоставлено, метод `reduce` вызывает функцию `callbackfn` для каждого элемента, начиная со второго.  
  
 Возвращаемое значение функции обратного вызова предоставляется как аргумент `previousValue` при следующем вызове функции обратного вызова.  Возвращаемое значение последнего вызова функции обратного вызова — возвращаемое значение метода `reduce`.  
  
 Функция обратного вызова не вызывается для отсутствующих элементов массива.  
  
> [!NOTE]
>  [Метод reduceRight \(Array\)](../../javascript/reference/reduceright-method-array-javascript.md) обрабатывает элементы в порядке убывания индекса.  
  
## Синтаксис функции обратного вызова  
 Синтаксис функции обратного вызова таков:  
  
 `function callbackfn(previousValue, currentValue, currentIndex, array1)`  
  
 Можно объявить функцию обратного вызова, используя до четырех параметров.  
  
 В приведенной ниже таблице перечислены параметры функции обратного вызова.  
  
|Аргумент обратного вызова|Определение|  
|-------------------------------|-----------------|  
|`previousValue`|Значение из предыдущего вызова функции обратного вызова.  Если значение `initialValue` предоставляется в метод `reduce`, то `previousValue` является значением `initialValue` при первом вызове функции.|  
|`currentValue`|Значение текущего элемента массива.|  
|`currentIndex`|Числовой индекс текущего элемента массива.|  
|`array1`|Объект массива, содержащий требуемый элемент.|  
  
## Первый вызов функции обратного вызова  
 При первом вызове функции обратного вызова значения, предоставляемые как аргументы, зависят от того, имеет ли метод `reduce` аргумент `initialValue`.  
  
 Если значение `initialValue` предоставляется методу reduce:  
  
-   Аргумент `previousValue` является `initialValue`.  
  
-   Аргумент `currentValue` является значением первого элемента, присутствующего в массиве.  
  
 Если `initialValue` не предоставлено:  
  
-   Аргумент `previousValue` является значением первого элемента, присутствующего в массиве.  
  
-   Аргумент `currentValue` является значением второго элемента, присутствующего в массиве.  
  
## Изменение объекта массива  
 Объект массива может изменяться функцией обратного вызова.  
  
 В следующей таблице описаны результаты изменения объекта массива после запуска метода `reduce`.  
  
|Условие после запуска метода `reduce`|Элемент передается функции обратного вызова?|  
|-------------------------------------------|--------------------------------------------------|  
|Элемент добавлен за пределами первоначальной длины массива.|Нет.|  
|Элемент добавлен для заполнения отсутствующего элемента массива.|Да, если этот индекс еще не был передан функции обратного вызова.|  
|Элемент изменен.|Да, если этот элемент еще не был передан функции обратного вызова.|  
|Элемент удален из массива.|Нет, если этот элемент не был уже передан функции обратного вызова.|  
  
## Пример  
 Следующий пример сцепляет значения массива в строку, разделяя значения знаками "::".  Поскольку начальное значение не предоставлено в метод `reduce`, первый вызов функции обратного вызова имеет значение "abc" в качестве аргумента `previousValue` и "def" в качестве аргумента `currentValue`.  
  
```javascript  
// Define the callback function.  
function appendCurrent (previousValue, currentValue) {  
    return previousValue + "::" + currentValue;  
    }  
  
// Create an array.  
var elements = ["abc", "def", 123, 456];  
  
// Call the reduce method, which calls the callback function  
// for each array element.  
var result = elements.reduce(appendCurrent);  
  
document.write(result);  
  
// Output:  
//  abc::def::123::456  
  
```  
  
## Пример  
 В следующем примере добавляются значения массива после округления.  Метод `reduce` вызывается с исходным значением 0.  
  
```javascript  
// Define the callback function.  
function addRounded (previousValue, currentValue) {  
    return previousValue + Math.round(currentValue);  
    }  
  
// Create an array.  
var numbers = [10.9, 15.4, 0.5];  
  
// Call the reduce method, starting with an initial value of 0.  
var result = numbers.reduce(addRounded, 0);  
  
document.write (result);  
// Output: 27  
```  
  
## Пример  
 В следующем примере значения добавляются в массив.  Параметры `currentIndex` и `array1` используются в функции обратного вызова.  
  
```javascript  
function addDigitValue(previousValue, currentDigit, currentIndex, array) {  
    var exponent = (array.length - 1) - currentIndex;  
    var digitValue = currentDigit * Math.pow(10, exponent);  
    return previousValue + digitValue;  
    }  
  
var digits = [4, 1, 2, 5];  
  
// Determine an integer that is computed from values in the array.  
var result = digits.reduce(addDigitValue, 0);  
  
document.write (result);  
// Output: 4125  
```  
  
## Пример  
 Следующий пример получает массив, который содержит только те значения, которые находятся в промежутке от 1 до 10 в другом массиве.  Начальное значение, предоставляемое методу `reduce`, является пустым массивом.  
  
```javascript  
function Process(previousArray, currentValue) {  
    // If currentValue is between 1 and 10,   
    // append currentValue to the array.  
    var nextArray;  
    if (currentValue >= 1 && currentValue <= 10)  
        nextArray = previousArray.concat(currentValue);  
    else  
        nextArray = previousArray;  
  
    // If this is not the last call by the reduce method,  
    // the returned array is previousArray on the next call.  
    // If this is the last call by the reduce method, the  
    // returned array is the return value of the reduce method.  
    return nextArray;  
}  
  
// Create an array.  
var numbers = [20, 1, -5, 6, 50, 3];  
  
// Call the reduce method, starting with an initial empty array.  
var emptyArray = new Array();  
var resultArray = numbers.reduce(Process, emptyArray);  
  
document.write("result array=" + resultArray);  
  
// Output:  
// result array=1,6,3  
```  
  
## Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## См. также  
 [Метод reduceRight \(Array\)](../../javascript/reference/reduceright-method-array-javascript.md)