---
title: "Массив объектов (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Array
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Array object
- constructor property
ms.assetid: 08e5f552-0797-4b48-8164-609582fc18c9
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a48d0ab5bac9d532e8fe8e356f4ea4df9e377b02
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="array-object-javascript"></a>Объект Array (JavaScript)
Предоставляет поддержку создания массивов любого типа данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```
arrayObj = new Array()  
arrayObj = new Array([size])  
arrayObj = new Array([element0[, element1[, ...[, elementN]]]])  
```  
  
## <a name="parameters"></a>Параметры  
 `arrayObj`  
 Обязательный. Имя переменной, которой присваивается объект `Array`.  
  
 `size`  
 Необязательно. Размер массива. Индексация массивов начинается с нуля: созданные элементы получают индексы от нуля до `size` - 1.  
  
 `element0,...,elementN`  
 Необязательно. Элементы, размещаемые в массиве. Создает массив с  *n*  + 1 элементов и `length` из  *n*  + 1. При использовании такого синтаксиса необходимо указать более одного элемента.  
  
## <a name="remarks"></a>Примечания  
 После создания массива можно получить доступ к его отдельным элементам с помощью нотации [ ]. Обратите внимание, что индексация массивов в [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] начинается с нуля.  
  
```JavaScript  
var my_array = new Array();  
for (i = 0; i < 10; i++) {  
    my_array[i] = i;  
}  
x = my_array[4];  
document.write(x);  
  
// Output: 4  
```  
  
 В конструктор `Array` можно передать 32-разрядное целое число без знака, чтобы указать размер массива. Если значение отрицательное или не является целым числом, возникает ошибка во время выполнения. При выполнении следующего кода эту ошибку можно увидеть в консоли.  
  
```JavaScript  
var arr = new Array(10);  
document.write(arr.length);  
  
// Output: 10  
  
// Don't do this  
var arr = new Array(-1);  
arr = new Array(1.50);   
```  
  
 Если в конструктор `Array` передается одно значение, не являющееся числом, свойству `length` задается значение 1, а значение единственного элемента будет единственным передаваемым аргументом.  
  
```npl  
var arr = new Array("one");  
document.write(arr.length);  
document.write("<br/>");  
document.write(arr[0]);  
  
// Output:  
1  
one  
  
```  
  
 Массивы JavaScript являются разреженными, то есть некоторые элементы массива могут не содержать данных. В JavaScript в массиве существуют только те элементы, которые действительно содержат данные. Это позволяет сократить объем памяти, используемой массивом.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 Некоторые члены в следующих списках были введены в более поздних версиях. Дополнительные сведения см. в разделе [сведения о версии](../../javascript/reference/javascript-version-information.md) или документации для отдельных членов.  
  
## <a name="properties"></a>Свойства  
 В следующей таблице перечислены свойства объекта `Array`.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|[Свойство constructor](../../javascript/reference/constructor-property-array.md)|Указывает функцию, которая создает массив.|  
|[Свойство length (массив)](../../javascript/reference/length-property-array-javascript.md)|Возвращает целочисленное значение, которое на единицу больше индекса последнего определенного элемента массива.|  
|[Свойство prototype](../../javascript/reference/prototype-property-array.md)|Возвращает ссылку на прототип массива.|  
  
## <a name="functions"></a>Функции  
 В следующей таблице описаны функции объекта `Array`.  
  
|Функция|Описание|  
|--------------|-----------------|  
|[Функция Array.FROM](../../javascript/reference/array-from-function-array-javascript.md)|Возвращает массив из итерируемого объекта или объекта, имеющего вид массива.|  
|[Функция Array.isArray](../../javascript/reference/array-isarray-function-javascript.md)|Возвращает логическое значение, указывающее, является ли объект массивом.|  
|[Функция Array.of](../../javascript/reference/array-of-function-array-javascript.md)|Возвращает массив из переданных аргументов.|  
  
<a name="js56jsobjarraymeth"></a>   
## <a name="methods"></a>Методы  
 В следующей таблице перечислены методы объекта `Array`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Метод concat (массив)](../../javascript/reference/concat-method-array-javascript.md)|Возвращает новый массив, состоящий из объединения двух массивов.|  
|[Метод Entries](../../javascript/reference/entries-method-array-javascript.md)|Возвращает итератор, который содержит пары "ключ- значение" массива.|  
|[Метод every](../../javascript/reference/every-method-array-javascript.md)|Проверяет, возвращает ли указанная функция обратного вызова `true` для всех элементов массива.|  
|[Метод Fill](../../javascript/reference/fill-method-array-javascript.md)|Заполняет массив указанным значением.|  
|[Метод filter](../../javascript/reference/filter-method-array-javascript.md)|Вызывает заданную функцию обратного вызова для каждого элемента массива и возвращает массив значений, для которых она возвращает `true`.|  
|[Метод findIndex](../../javascript/reference/findindex-method-array-javascript.md)|Возвращает значение индекса для первого элемента массива, который соответствует тестовым критериям, указанным в функции обратного вызова.|  
|[Метод forEach](../../javascript/reference/foreach-method-array-javascript.md)|Вызывает заданную функцию обратного вызова для каждого элемента массива.|  
|[Метод hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Возвращает логическое значение, указывающее, содержит ли объект свойство с указанным именем.|  
|[Метод indexOf (массив)](../../javascript/reference/indexof-method-array-javascript.md)|Возвращает индекс первого вхождения значения в массиве.|  
|[Метод isPrototypeOf](../../javascript/reference/isprototypeof-method-object-javascript.md)|Возвращает логическое значение, указывающее, существует ли объект в другом объекте цепочки прототипов.|  
|[Метод join](../../javascript/reference/join-method-array-javascript.md)|Возвращает объект `String`, состоящий из всех элементов массива, соединенных вместе.|  
|[Метод Keys](../../javascript/reference/keys-method-array-javascript.md)|Возвращает итератор, который содержит значения индексов массива.|  
|[Метод lastIndexOf (массив)](../../javascript/reference/lastindexof-method-array-javascript.md)|Возвращает индекс последнего вхождения указанного значения в массиве.|  
|[Метод map](../../javascript/reference/map-method-array-javascript.md)|Вызывает заданную функцию обратного вызова для каждого элемента массива и возвращает массив, содержащий результаты.|  
|[Метод pop](../../javascript/reference/pop-method-array-javascript.md)|Удаляет последний элемент из массива и возвращает его.|  
|[Метод propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Возвращает логическое значение, определяющее, является ли указанное свойство частью объекта, и является ли оно перечислимым.|  
|[Метод push](../../javascript/reference/push-method-array-javascript.md)|Присоединяет новые элементы к массиву и возвращает новую длину массива.|  
|[Метод reduce](../../javascript/reference/reduce-method-array-javascript.md)|Накапливает единый результат посредством вызова заданной функции обратного вызова для всех элементов массива. Возвращаемое значение функции обратного вызова — накопленный результат. Оно предоставляется как аргумент в следующем вызове функции обратного вызова.|  
|[Метод reduceRight](../../javascript/reference/reduceright-method-array-javascript.md)|Накапливает единый результат посредством вызова заданной функции обратного вызова для всех элементов массива в порядке убывания индекса. Возвращаемое значение функции обратного вызова — накопленный результат. Оно предоставляется как аргумент в следующем вызове функции обратного вызова.|  
|[Метод reverse](../../javascript/reference/reverse-method-javascript.md)|Возвращает объект `Array` с обратным порядком элементов.|  
|[Метод shift](../../javascript/reference/shift-method-array-javascript.md)|Удаляет первый элемент из массива и возвращает его.|  
|[Метод slice (массив)](../../javascript/reference/slice-method-array-javascript.md)|Возвращает фрагмент массива.|  
|[Метод some](../../javascript/reference/some-method-array-javascript.md)|Проверяет, возвращает ли заданная функция обратного вызова значение `true` для какого-либо элемента массива.|  
|[Метод sort](../../javascript/reference/sort-method-array-javascript.md)|Возвращает объект `Array` с упорядоченными элементами.|  
|[Метод splice](../../javascript/reference/splice-method-array-javascript.md)|Удаляет элементы из массива и при необходимости вставляет на их место новые элементы, возвращая удаленные элементы.|  
|[Метод toLocaleString](../../javascript/reference/tolocalestring-method-object-javascript.md)|Возвращает строку с использованием текущего языкового стандарта.|  
|[Метод toString](../../javascript/reference/tostring-method-array.md)|Возвращает строковое представление массива.|  
|[Метод unshift](../../javascript/reference/unshift-method-array-javascript.md)|Вставляет новые элементы в начало массива.|  
|[Метод valueOf](../../javascript/reference/valueof-method-array.md)|Получает ссылку на массив.|  
|[Метод Values](../../javascript/reference/values-method-array-javascript.md)|Возвращает итератор, который содержит значения массива.|  
  
## <a name="see-also"></a>См. также  
 [Прокрутки, сдвига и масштабирования примера приложения](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)