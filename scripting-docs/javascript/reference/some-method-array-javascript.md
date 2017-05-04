---
title: "Метод some (Array) (JavaScript) | Microsoft Docs"
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
  - "массивы [JavaScript], some - метод"
  - "some - метод [JavaScript]"
ms.assetid: 7b6822f9-c406-4f4e-bfec-a93459745992
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Метод some (Array) (JavaScript)
Определяет, возвращает ли заданная функция обратного вызова значение `true` для какого\-либо элемента массива.  
  
## Синтаксис  
  
```  
  
array1.some(callbackfn[, thisArg])  
```  
  
#### Параметры  
  
|Параметр|Определение|  
|--------------|-----------------|  
|`array1`|Обязательный.  Объект массива.|  
|`callbackfn`|Обязательный.  Функция, принимающая до трех аргументов.  Метод `some` вызывает функцию `callbackfn` для каждого элемента в массиве `array1`, пока функция `callbackfn` не вернет значение `true` или не будет достигнут конец массива.|  
|`thisArg`|Необязательный.  Объект, на который может ссылаться ключевое слово `this` в функции `callbackfn`.  Если аргумент `thisArg` опущен, в качестве значения `this` используется `undefined`.|  
  
## Возвращаемое значение  
 Значение `true`, если функция `callbackfn` возвращает значение `true` для какого\-либо элемента массива; в противном случае — значение `false`.  
  
## Исключения  
 Если аргумент `callbackfn` не является объектом функции, вызывается исключение `TypeError`.  
  
## Заметки  
 Метод `some` вызывает функцию `callbackfn` для каждого элемента массива \(в порядке возрастания индекса\), пока функция `callbackfn` не вернет значение `true`.  Если элемент, для которого функция `callbackfn` возвращает значение `true`, найден, метод `some` немедленно возвращает значение `true`.  Если обратный вызов не возвращает значения `true` ни для одного элемента, метод `some` возвращает значение `false`.  
  
 Функция обратного вызова не вызывается для отсутствующих элементов массива.  
  
 Помимо объектов массива, метод `some` может использоваться любым объектом, имеющим свойство `length` и обладающим численно проиндексированными именами свойств.  
  
> [!NOTE]
>  [Метод every \(Array\)](../../javascript/reference/every-method-array-javascript.md) позволяет проверить, возвращает ли функция обратного вызова значение `true` для всех элементов массива.  
  
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
  
 В следующей таблице описаны результаты изменения объекта массива после запуска метода `some`.  
  
|Условие после запуска метода `some`|Элемент передается функции обратного вызова?|  
|-----------------------------------------|--------------------------------------------------|  
|Элемент добавлен за пределами первоначальной длины массива.|Нет.|  
|Элемент добавлен для заполнения отсутствующего элемента массива.|Да, если этот индекс еще не был передан функции обратного вызова.|  
|Элемент изменен.|Да, если этот элемент еще не был передан функции обратного вызова.|  
|Элемент удален из массива.|Нет, если этот элемент не был уже передан функции обратного вызова.|  
  
## Пример  
 В следующем примере используется метод `some`, чтобы выяснить, есть ли в массиве равные элементы  
  
```javascript  
// The callback function.  
function CheckIfEven(value, index, ar) {  
    if (value % 2 == 0)  
        return true;  
}  
  
var numbers = [1, 15, 4, 10, 11, 22];  
  
var evens = numbers.some(CheckIfEven);  
document.write(evens);  
  
// Output:  
// true  
```  
  
## Пример  
 В следующем примере показано использование параметра `thisArg`, задающего объект, к которому может относиться ключевое слово `this`.  Выполняется проверка, есть ли в массиве числа, находящиеся вне диапазона, предоставленного переданным объектом  
  
```javascript  
// Create a function that returns true if the value is   
// outside the range.  
var isOutsideRange = function (value) {  
    return value < this.minimum || value > this.maximum;  
}  
  
// Create an array of numbers.  
var numbers = [6, 12, 16, 22, -12];  
  
// The range object is to be the 'this' object.  
var range = { minimum: 10, maximum: 20 };  
  
document.write(numbers.some(isOutsideRange, range));  
  
// Output: true  
  
```  
  
## Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## См. также  
 [Метод every \(Array\)](../../javascript/reference/every-method-array-javascript.md)   
 [Метод filter \(Array\)](../../javascript/reference/filter-method-array-javascript.md)   
 [Метод map \(Array\)](../../javascript/reference/map-method-array-javascript.md)