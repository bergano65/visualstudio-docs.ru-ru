---
title: "Метод reduceRight (Array) (JavaScript) | Microsoft Docs"
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
  - "массивы [JavaScript], reduceRight - метод"
  - "reduceRight - метод [JavaScript]"
ms.assetid: 85963761-da11-407c-8bce-278c930e61bd
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Метод reduceRight (Array) (JavaScript)
Вызывает заданную функцию обратного вызова для всех элементов в массиве в порядке убывания.  Возвращаемое значение функции обратного вызова представляет собой накопленный результат и предоставляется как аргумент в следующем вызове функции обратного вызова.  
  
## Синтаксис  
  
```  
  
array1.reduceRight(callbackfn[, initialValue])  
```  
  
#### Параметры  
  
|Параметр|Определение|  
|--------------|-----------------|  
|`array1`|Обязательный.  Объект массива.|  
|`callbackfn`|Обязательный.  Функция, которая принимает до четырех аргументов.  Метод `reduceRight` вызывает функцию `callbackfn` по одному разу для каждого элемента массива.|  
|`initialValue`|Необязательный.  Если значение `initialValue` указано, оно используется в качестве начального значения, с которого начинается накопление.  При первом вызове функции `callbackfn` в качестве аргумента вместо значения из массива предоставляется это значение.|  
  
## Возвращаемое значение  
 Объект, содержащий накопленный результат последнего вызова функции обратного вызова.  
  
## Исключения  
 Исключение `TypeError` возникает, если выполняется одно из следующих условий.  
  
-   Аргумент `callbackfn` не является объектом функции.  
  
-   Массив не содержит элементов и `initialValue` не предоставлено.  
  
## Заметки  
 Если значение `initialValue` предоставлено, метод `reduceRight` вызывает функцию `callbackfn` по одному разу для каждого элемента массива в порядке убывания индекса.  Если значение `initialValue` не предоставлено, метод `reduceRight` вызывает функцию `callbackfn` для каждого элемента, начиная с предпоследнего, в порядке убывания индекса.  
  
 Возвращаемое значение функции обратного вызова предоставляется как аргумент `previousValue` при следующем вызове функции обратного вызова.  Возвращаемое значение последнего вызова функции обратного вызова — возвращаемое значение метода `reduceRight`.  
  
 Функция обратного вызова не вызывается для отсутствующих элементов массива.  
  
 Чтобы накапливать результат в порядке возрастания индекса, используйте [Метод reduce \(Array\)](../../javascript/reference/reduce-method-array-javascript.md).  
  
## Синтаксис функции обратного вызова  
 Синтаксис функции обратного вызова таков:  
  
 `function callbackfn(previousValue, currentValue, currentIndex, array1)`  
  
 Можно объявить функцию обратного вызова, используя до четырех параметров.  
  
 В приведенной ниже таблице перечислены параметры функции обратного вызова.  
  
|Аргумент обратного вызова|Определение|  
|-------------------------------|-----------------|  
|`previousValue`|Значение из предыдущего вызова функции обратного вызова.  Если значение `initialValue` предоставляется в метод `reduceRight`, то `previousValue` является значением `initialValue` при первом вызове функции.|  
|`currentValue`|Значение текущего элемента массива.|  
|`currentIndex`|Числовой индекс текущего элемента массива.|  
|`array1`|Объект массива, содержащий требуемый элемент.|  
  
## Первый вызов функции обратного вызова  
 При первом вызове функции обратного вызова значения, предоставляемые как аргументы, зависят от того, имеет ли метод `reduceRight` аргумент `initialValue`.  
  
 Если значение `initialValue` предоставлено методу `reduceRight`:  
  
-   Аргумент `previousValue` является `initialValue`.  
  
-   Аргумент `currentValue` является значением последнего элемента, присутствующего в массиве.  
  
 Если `initialValue` не предоставлено:  
  
-   Аргумент `previousValue` является значением последнего элемента, присутствующего в массиве.  
  
-   Аргумент `currentValue` является значением предпоследнего элемента, присутствующего в массиве.  
  
## Изменение объекта массива  
 Объект массива может изменяться функцией обратного вызова.  
  
 В следующей таблице описаны результаты изменения объекта массива после запуска метода `reduceRight`.  
  
|Условие после запуска метода `reduceRight`|Элемент передается функции обратного вызова?|  
|------------------------------------------------|--------------------------------------------------|  
|Элемент добавлен за пределами первоначальной длины массива.|Нет.|  
|Элемент добавлен для заполнения отсутствующего элемента массива.|Да, если этот индекс еще не был передан функции обратного вызова.|  
|Элемент изменен.|Да, если этот элемент еще не был передан функции обратного вызова.|  
|Элемент удален из массива.|Нет, если этот элемент не был уже передан функции обратного вызова.|  
  
## Пример  
 Следующий пример сцепляет значения массива в строку, разделяя значения знаками "::".  Поскольку начальное значение не предоставлено в метод `reduceRight`, первый вызов функции обратного вызова использует значение 456 в качестве аргумента `previousValue` и 123 в качестве аргумента `currentValue`.  
  
```javascript  
// Define the callback function.  
function appendCurrent (previousValue, currentValue) {  
    return previousValue + "::" + currentValue;  
    }  
  
// Create an array.  
var elements = ["abc", "def", 123, 456];  
  
// Call the reduceRight method, which calls the callback function  
// for each array element, in descending index order.  
var result = elements.reduceRight(appendCurrent);  
  
document.write(result);  
  
// Output:  
//  456::123::def::abc  
```  
  
## Пример  
 В следующем примере находится сумма квадратов элементов массива.  Метод `reduceRight` вызывается с исходным значением 0.  
  
```javascript  
// Define the callback function.  
function Process(previousValue, currentValue, index, array) {  
    // Add the previous value to the current value squared.  
    var nextValue = previousValue + (currentValue * currentValue);  
  
    // If this is not the last call by the reduceRight method,  
    // the return value is previousValue on the next call.  
    // If this is the last call by the reduceRight method, the  
    // return value is the return value of the reduceRight method.  
    return nextValue;  
}  
  
// Create an array.  
var numbers = [3, 4, 5];  
  
// Call the reduceRight method with an initial value of 0.  
var sumOfSquares = numbers.reduceRight(Process, 0);  
  
document.write("sum of squares=" + sumOfSquares);  
  
// Output:  
//  sum of squares=50  
```  
  
## Пример  
 В следующем примере получаются те элементы массива, значения которых лежат в диапазоне от 1 до 10.  Начальное значение, предоставляемое методу `reduceRight`, является пустым массивом.  
  
```javascript  
function Process2(previousArray, currentValue) {  
    // If currentValue is between 1 and 10,   
    // append currentValue to the array.  
    var nextArray;  
    if (currentValue >= 1 && currentValue <= 10)  
        nextArray = previousArray.concat(currentValue);  
    else  
        nextArray = previousArray;  
  
    // If this is not the last call by the reduceRight method,  
    // the returned array is previousArray on the next call.  
    // If this is the last call by the reduceRight method, the  
    // returned array is the return value of the reduceRight method.  
    return nextArray;  
}  
  
// Create an array.  
var numbers = [20, 1, -5, 6, 50, 3];  
  
// Call the reduceRight method, starting with an empty array.  
var emptyArray = new Array();  
var resultArray = numbers.reduceRight(Process2, emptyArray);  
  
document.write("result array=" + resultArray);  
  
// Output:  
//  result array=3,6,1  
```  
  
## Пример  
 Метод `reduceRight` может быть применен к строке.  В следующем примере показано, как использовать этот метод для изменения порядка символов в строке.  
  
```javascript  
// Define the callback function.  
function AppendToArray(previousValue, currentValue) {  
    return previousValue + currentValue;  
}  
  
var word = "retupmoc";  
  
// Create a string that reverses the characters of another string.  
// The commented-out statement shows an alternative syntax.  
var result = [].reduceRight.call(word, AppendToArray, "the ");  
// var result = Array.prototype.reduceRight.call(word, AppendToArray, "the ");  
  
document.write(result);  
  
// Output:  
// the computer  
```  
  
## Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## См. также  
 [Метод reduce \(Array\)](../../javascript/reference/reduce-method-array-javascript.md)