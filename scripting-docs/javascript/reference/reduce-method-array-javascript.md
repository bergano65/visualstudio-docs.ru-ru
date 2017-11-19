---
title: "Метод Reduce (Array) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- callback function, reduce method [JavaScript]
- arrays [JavaScript], reduce method
- reduce method [JavaScript]
ms.assetid: 48d069e0-e083-494f-86d5-d459d2377dc5
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76279f66f8e3180fdebd73b83eb31c7368cefc75
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="reduce-method-array-javascript"></a>Метод reduce (Array) (JavaScript)
Вызывает заданный обратный вызов функции для всех элементов в массиве. Возвращаемое значение функции обратного вызова — накопленный результат. Оно предоставляется как аргумент в следующем вызове функции обратного вызова.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
array1.reduce(callbackfn[, initialValue])  
```  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Определение|  
|---------------|----------------|  
|`array1`|Обязательный. Объект массива.|  
|`callbackfn`|Обязательный. Функция, которая принимает до четырех аргументов. Метод `reduce` вызывает функцию `callbackfn` по одному разу для каждого элемента массива.|  
|`initialValue`|Необязательно. Если `initialValue` указан, он используется как начальное значение для запуска этих копий. Первый вызов `callbackfn` функции это значение предоставляется как аргумент вместо значения массива.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Накопленный результат из последнего вызова функции обратного вызова.  
  
## <a name="exceptions"></a>Исключения  
 Объект `TypeError` исключение создается при выполнении одного из следующих условий:  
  
-   `callbackfn` Аргумент не является объектом функции.  
  
-   Массив не содержит элементов и `initialValue` не предоставляется.  
  
## <a name="remarks"></a>Примечания  
 Если `initialValue` предоставляется, `reduce` вызовы метода `callbackfn` функцию один раз для каждого элемента массива в порядке возрастания индекса. Если `initialValue` не предоставлен, `reduce` вызовы метода `callbackfn` функции к каждому элементу, начиная со второго элемента.  
  
 Возвращаемое значение функции обратного вызова предоставляется как `previousValue` аргумента при следующем вызове функции обратного вызова. Возвращаемое значение последнего вызова функции обратного вызова имеет значение, возвращаемое `reduce` метод.  
  
 Функция обратного вызова не вызывается для отсутствующих элементов массива.  
  
> [!NOTE]
>  [Метод reduceRight (Array)](../../javascript/reference/reduceright-method-array-javascript.md) обрабатывает элементы в порядке убывания индекса.  
  
## <a name="callback-function-syntax"></a>Синтаксис функции обратного вызова  
 Синтаксис функции обратного вызова выглядит следующим образом:  
  
 `function callbackfn(previousValue, currentValue, currentIndex, array1)`  
  
 Функция обратного вызова можно объявить с помощью до четырех параметров.  
  
 В следующей таблице перечислены параметры функции обратного вызова.  
  
|Аргумент обратного вызова|Определение|  
|-----------------------|----------------|  
|`previousValue`|Значение из предыдущего вызова функции обратного вызова. Если `initialValue` передается `reduce` метода `previousValue` — `initialValue` при первом вызове функции.|  
|`currentValue`|Значение текущего элемента массива.|  
|`currentIndex`|Числовой индекс текущего элемента массива.|  
|`array1`|Объект массива, содержащий требуемый элемент.|  
  
## <a name="first-call-to-the-callback-function"></a>Первый вызов функции обратного вызова  
 При первом вызове функции обратного вызова, значений, предоставленных как аргументы зависят ли `reduce` имеет метод `initialValue` аргумент.  
  
 Если `initialValue` предоставляется методу сократить:  
  
-   Аргумент `previousValue` имеет значение `initialValue`.  
  
-   `currentValue` Аргумент имеет значение первого элемента массива.  
  
 Если `initialValue` не задан:  
  
-   `previousValue` Аргумент имеет значение первого элемента массива.  
  
-   `currentValue` Аргумент имеет значение второго элемента массива.  
  
## <a name="modifying-the-array-object"></a>Изменение объекта массива  
 Объект массива может изменяться функцией обратного вызова.  
  
 В следующей таблице описаны результаты изменения объекта массива после запуска метода `reduce`.  
  
|Условие после запуска метода `reduce`|Элемент передается функции обратного вызова?|  
|------------------------------------------------|------------------------------------------|  
|Элемент добавлен за пределами первоначальной длины массива.|Нет.|  
|Элемент добавлен для заполнения отсутствующего элемента массива.|Да, если этот индекс еще не был передан функции обратного вызова.|  
|Элемент изменен.|Да, если этот элемент еще не был передан функции обратного вызова.|  
|Элемент удален из массива.|Нет, если этот элемент не был уже передан функции обратного вызова.|  
  
## <a name="example"></a>Пример  
 Следующий пример объединяет значения массива в строку, разделяя значения с «::». Так как начальное значение не указано для `reduce` метод, первый вызов функции обратного вызова имеет «abc» как `previousValue` аргумент и «def» как `currentValue` аргумент.  
  
```JavaScript  
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
  
## <a name="example"></a>Пример  
 В следующем примере добавляется значения массива после они были округлены. `reduce` Метод вызывается с исходным значением 0.  
  
```JavaScript  
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
  
## <a name="example"></a>Пример  
 Следующий пример добавляет значения в массиве. `currentIndex` И `array1` параметры используются в функции обратного вызова.  
  
```JavaScript  
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
  
## <a name="example"></a>Пример  
 Следующий пример возвращает массив, содержащий только те значения, которые находятся в диапазоне от 1 до 10 в другом массиве. Начальное значение, указанное для `reduce` метод — пустой массив.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Метод reduceRight (Array)](../../javascript/reference/reduceright-method-array-javascript.md)