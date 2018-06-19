---
title: Метод Every (Array) (JavaScript) | Документы Microsoft
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
- every method
- arrays [JavaScript], every method
ms.assetid: dc4ee2f8-fb9e-4c9f-af5a-fe836e40ddd1
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a05263ae45df61c47a3580d474863c8d4ff3dd1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637404"
---
# <a name="every-method-array-javascript"></a>Метод every (Array) (JavaScript)
Определяет, удовлетворяют ли все элементы массива заданному тесту.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
array1.every(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Определение|  
|---------------|----------------|  
|`array1`|Обязательный. Объект массива.|  
|`callbackfn`|Обязательный. Функция, которая принимает до 3 аргументов. `every` Вызовы метода `callbackfn` функции для каждого элемента в `array1` до `callbackfn` возвращает `false`, или до конца массива.|  
|`thisArg`|Необязательно. Объект, на который может ссылаться ключевое слово `this` в функции `callbackfn`. Если параметр `thisArg` опущен, в качестве значения `undefined` используется `this`.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 `true`Если `callbackfn` возврата функцией `true` для всех массивов элементов; в противном случае `false`. Если массив не содержит элементов, `every` возвращает `true`.  
  
## <a name="exceptions"></a>Исключения  
 Если аргумент `callbackfn` не является объектом функции, вызывается исключение `TypeError`.  
  
## <a name="remarks"></a>Примечания  
 `every` Вызовы метода `callbackfn` функцию один раз для каждого элемента массива в порядке возрастания индекса, пока `callbackfn` возврата функцией `false`. Если элемент, который вызывает `callbackfn` для возврата `false` найден, `every` метод немедленно возвращает `false`. В противном случае `every` возвращает `true`.  
  
 Функция обратного вызова не вызывается для отсутствующих элементов массива.  
  
 Помимо объектов массива, метод `every` может использоваться любым объектом, имеющим свойство `length` и обладающим численно проиндексированными именами свойств.  
  
> [!NOTE]
>  Можно использовать [метод some (Array)](../../javascript/reference/some-method-array-javascript.md) Чтобы проверить, возвращает ли функция обратного вызова `true` для любого элемента массива.  
  
## <a name="callback-function-syntax"></a>Синтаксис функции обратного вызова  
 Синтаксис функции обратного вызова выглядит следующим образом:  
  
 `function callbackfn(value, index, array1)`  
  
 Можно объявить функцию обратного вызова с до трех параметров.  
  
 В следующей таблице перечислены параметры функции обратного вызова.  
  
|Параметр обратного вызова|Определение|  
|------------------------|----------------|  
|`value`|Значение элемента массива.|  
|`index`|Числовой индекс элемента массива.|  
|`array1`|Объект массива, содержащий требуемый элемент.|  
  
## <a name="modifying-the-array-object"></a>Изменение объекта массива  
 Объект массива может изменяться функцией обратного вызова.  
  
 В следующей таблице описаны результаты изменения объекта массива после запуска метода `every`.  
  
|Условие после запуска метода `every`|Элемент передается функции обратного вызова?|  
|-----------------------------------------------|------------------------------------------|  
|Элемент добавлен за пределами первоначальной длины массива.|Нет.|  
|Элемент добавлен для заполнения отсутствующего элемента массива.|Да, если этот индекс еще не был передан функции обратного вызова.|  
|Элемент изменен.|Да, если этот элемент еще не был передан функции обратного вызова.|  
|Элемент удален из массива.|Нет, если этот элемент не был уже передан функции обратного вызова.|  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода `every`.  
  
```JavaScript  
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
  
## <a name="example"></a>Пример  
 В следующем примере показано использование аргумента `thisArg`, задающего объект, на который может ссылаться ключевое слово `this`.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Метод Some (Array)](../../javascript/reference/some-method-array-javascript.md)   
 [Метод Filter (Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [Объект Array](../../javascript/reference/array-object-javascript.md)   
 [Использование массивов](../../javascript/advanced/using-arrays-javascript.md)