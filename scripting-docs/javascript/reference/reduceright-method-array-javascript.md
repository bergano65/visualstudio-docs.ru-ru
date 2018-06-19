---
title: Метод reduceRight (Array) (JavaScript) | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [JavaScript], reduceRight method
- reduceRight method [JavaScript]
ms.assetid: 85963761-da11-407c-8bce-278c930e61bd
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d7fd2794157eadacefa7404f9333c51aed9425c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641924"
---
# <a name="reduceright-method-array-javascript"></a>Метод reduceRight (Array) (JavaScript)
Вызывает заданный обратный вызов функции для всех элементов в массиве, в порядке убывания. Возвращаемое значение функции обратного вызова — накопленный результат. Оно предоставляется как аргумент в следующем вызове функции обратного вызова.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
array1.reduceRight(callbackfn[, initialValue])  
```  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Определение|  
|---------------|----------------|  
|`array1`|Обязательный. Объект массива.|  
|`callbackfn`|Обязательный. Функция, которая принимает до четырех аргументов. Метод `reduceRight` вызывает функцию `callbackfn` по одному разу для каждого элемента массива.|  
|`initialValue`|Необязательно. Если `initialValue` указан, он используется как начальное значение для запуска этих копий. Первый вызов `callbackfn` функции это значение предоставляется как аргумент вместо значения массива.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект, содержащий накопленный результат из последнего вызова функции обратного вызова.  
  
## <a name="exceptions"></a>Исключения  
 Объект `TypeError` исключение создается при выполнении одного из следующих условий:  
  
-   `callbackfn` Аргумент не является объектом функции.  
  
-   Массив не содержит элементов и `initialValue` не предоставляется.  
  
## <a name="remarks"></a>Примечания  
 Если `initialValue` предоставляется, `reduceRight` вызовы метода `callbackfn` функцию один раз для каждого элемента в массиве, в порядке убывания индекса. Если не `initialValue` предоставляется, `reduceRight` вызовы метода `callbackfn` функции к каждому элементу, начиная с с последним второго элемента, в порядке убывания индекса.  
  
 Возвращаемое значение функции обратного вызова предоставляется как `previousValue` аргумента при следующем вызове функции обратного вызова. Возвращаемое значение последнего вызова функции обратного вызова имеет значение, возвращаемое `reduceRight` метод.  
  
 Функция обратного вызова не вызывается для отсутствующих элементов массива.  
  
 Накапливать результат в порядке возрастания индекса, используйте [метод reduce (Array)](../../javascript/reference/reduce-method-array-javascript.md).  
  
## <a name="callback-function-syntax"></a>Синтаксис функции обратного вызова  
 Синтаксис функции обратного вызова выглядит следующим образом:  
  
 `function callbackfn(previousValue, currentValue, currentIndex, array1)`  
  
 Функция обратного вызова можно объявить с помощью до четырех параметров.  
  
 В следующей таблице перечислены параметры функции обратного вызова.  
  
|Аргумент обратного вызова|Определение|  
|-----------------------|----------------|  
|`previousValue`|Значение из предыдущего вызова функции обратного вызова. Если `initialValue` передается `reduceRight` метода `previousValue` — `initialValue` при первом вызове функции.|  
|`currentValue`|Значение текущего элемента массива.|  
|`currentIndex`|Числовой индекс текущего элемента массива.|  
|`array1`|Объект массива, содержащий требуемый элемент.|  
  
## <a name="first-call-to-the-callback-function"></a>Первый вызов функции обратного вызова  
 При первом вызове функции обратного вызова, значений, предоставленных как аргументы зависят ли `reduceRight` имеет метод `initialValue` аргумент.  
  
 Если `initialValue` передается `reduceRight` метод:  
  
-   Аргумент `previousValue` имеет значение `initialValue`.  
  
-   `currentValue` Аргумент является значением последнего элемента массива.  
  
 Если `initialValue` не задан:  
  
-   `previousValue` Аргумент является значением последнего элемента массива.  
  
-   `currentValue` Аргумент имеет значение секунду для последнего элемента массива.  
  
## <a name="modifying-the-array-object"></a>Изменение объекта массива  
 Объект массива может изменяться функцией обратного вызова.  
  
 В следующей таблице описаны результаты изменения объекта массива после запуска метода `reduceRight`.  
  
|Условие после запуска метода `reduceRight`|Элемент передается функции обратного вызова?|  
|-----------------------------------------------------|------------------------------------------|  
|Элемент добавлен за пределами первоначальной длины массива.|Нет.|  
|Элемент добавлен для заполнения отсутствующего элемента массива.|Да, если этот индекс еще не был передан функции обратного вызова.|  
|Элемент изменен.|Да, если этот элемент еще не был передан функции обратного вызова.|  
|Элемент удален из массива.|Нет, если этот элемент не был уже передан функции обратного вызова.|  
  
## <a name="example"></a>Пример  
 Следующий пример объединяет значения массива в строку, разделяя значения с «::». Так как начальное значение не указано для `reduceRight` метод, первый вызов функции обратного вызова имеет 456 как `previousValue` аргумент и 123 в качестве `currentValue` аргумент.  
  
```JavaScript  
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
  
## <a name="example"></a>Пример  
 В следующем примере вычисляется сумма квадратов элементов массива. `reduceRight` Метод вызывается с исходным значением 0.  
  
```JavaScript  
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
  
## <a name="example"></a>Пример  
 В следующем примере извлекается этих элементов в массиве, значения которых находятся в диапазоне от 1 до 10. Начальное значение, указанное для `reduceRight` метод — пустой массив.  
  
```JavaScript  
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
  
## <a name="example"></a>Пример  
 Метод `reduceRight` может быть применен к строке. В следующем примере показано применение этого метода для отмены символов в строке.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Метод reduce (Array)](../../javascript/reference/reduce-method-array-javascript.md)