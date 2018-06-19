---
title: Метод Some (Array) (JavaScript) | Документы Microsoft
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
- arrays [JavaScript], some method
- some method [JavaScript]
ms.assetid: 7b6822f9-c406-4f4e-bfec-a93459745992
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba3f855c61daac511bcf7aca6b47f643dda93313
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641764"
---
# <a name="some-method-array-javascript"></a>Метод some (Array) (JavaScript)
Определяет, возвращает ли функция обратного вызова указанного `true` для любого элемента массива.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
array1.some(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Определение|  
|---------------|----------------|  
|`array1`|Обязательный. Объект массива.|  
|`callbackfn`|Обязательный. Функция, которая принимает до 3 аргументов. `some` Вызовы метода `callbackfn` функции для каждого элемента в `array1` до `callbackfn` возвращает `true`, или до конца массива.|  
|`thisArg`|Необязательно. Объект, на который может ссылаться ключевое слово `this` в функции `callbackfn`. Если параметр `thisArg` опущен, в качестве значения `undefined` используется `this`.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 `true`Если `callbackfn` возврата функцией `true` для любого элемента массива; в противном случае `false`.  
  
## <a name="exceptions"></a>Исключения  
 Если аргумент `callbackfn` не является объектом функции, вызывается исключение `TypeError`.  
  
## <a name="remarks"></a>Примечания  
 `some` Вызовы метода `callbackfn` функции для каждого элемента массива, в порядке возрастания индекса, пока `callbackfn` возврата функцией `true`. Если элемент, который вызывает `callbackfn` для возврата `true` найден, `some` метод немедленно возвращает `true`. Если обратный вызов не возвращает `true` для любого элемента `some` возвращает `false`.  
  
 Функция обратного вызова не вызывается для отсутствующих элементов массива.  
  
 Помимо объектов массива, метод `some` может использоваться любым объектом, имеющим свойство `length` и обладающим численно проиндексированными именами свойств.  
  
> [!NOTE]
>  Можно использовать [метод every (Array)](../../javascript/reference/every-method-array-javascript.md) Чтобы проверить, возвращает ли функция обратного вызова `true` для всех элементов массива.  
  
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
  
 В следующей таблице описаны результаты изменения объекта массива после запуска метода `some`.  
  
|Условие после запуска метода `some`|Элемент передается функции обратного вызова?|  
|----------------------------------------------|------------------------------------------|  
|Элемент добавлен за пределами первоначальной длины массива.|Нет.|  
|Элемент добавлен для заполнения отсутствующего элемента массива.|Да, если этот индекс еще не был передан функции обратного вызова.|  
|Элемент изменен.|Да, если этот элемент еще не был передан функции обратного вызова.|  
|Элемент удален из массива.|Нет, если этот элемент не был уже передан функции обратного вызова.|  
  
## <a name="example"></a>Пример  
 В следующем примере используется `some` метод, чтобы определить какие-либо элементы массива являются четными.  
  
```JavaScript  
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
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать `thisArg` параметр, который указывает объект, к которому `this` может ссылаться ключевое слово. Проверяет, находятся ли какие-либо числа в виде массива вне диапазона, предоставляемые объекта, передаваемого  
  
```JavaScript  
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
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Метод Every (Array)](../../javascript/reference/every-method-array-javascript.md)   
 [Метод Filter (Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [Метод map (Array)](../../javascript/reference/map-method-array-javascript.md)