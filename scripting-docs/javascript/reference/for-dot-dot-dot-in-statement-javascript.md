---
title: "for... в инструкции (JavaScript) | Документы Microsoft"
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
- iteration statements, for...in statement
- loop structures, for...in statements
ms.assetid: 1b51a0ce-89f7-4a69-88ed-017b47dc398f
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9c3ce78def6ab91256ff724a4acc87b7cf19ba2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="forin-statement-javascript"></a>Оператор for...in (JavaScript)
Выполняет один или несколько операторов для каждого свойства объекта или каждого элемента массива.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
for (variable in [object | array]) {  
    statements   
}  
```  
  
## <a name="parameters"></a>Параметры  
 `variable`  
 Обязательный. Переменную, которая может быть любое имя свойства объекта `object` или любой элемент индекс `array`.  
  
 `object`, `array`  
 Необязательно. Объект или массив, по которому выполняется итерация.  
  
 `statements`  
 Необязательно. Один или несколько операторов для выполнения для каждого свойства `object` или каждого элемента `array`. Может быть составным оператором.  
  
## <a name="remarks"></a>Примечания  
 В начале каждой итерации цикла, а значение `variable` имеет следующее имя свойства объекта `object` или Далее индекс элемента `array`. Затем можно использовать `variable` в любой из инструкций внутри цикла для ссылки на свойство объекта `object` или элемент `array`.  
  
 Свойства объекта, не назначаются в определенном режиме. Нельзя указать конкретного свойства по его индексу только по имени свойства.  
  
 Перебор массива выполняется по порядку, то есть 0, 1, 2.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование `for...in` для объекта, который используется в качестве ассоциативного массива.  
  
```JavaScript  
// Initialize object.  
a = {"a" : "Athens" , "b" : "Belgrade", "c" : "Cairo"}  
  
// Iterate over the properties.  
var s = ""  
for (var key in a) {  
    s += key + ": " + a[key];  
    s += "<br />";  
    }  
document.write (s);  
  
// Output:  
// a: Athens  
// b: Belgrade  
// c: Cairo  
```  
  
## <a name="example"></a>Пример  
 В этом примере показано использование `for ... in` оператора итерации `Array` объекта, имеющего свойств expando.  
  
```JavaScript  
// Initialize the array.  
var arr = new Array("zero","one","two");  
  
// Add a few expando properties to the array.  
arr["orange"] = "fruit";  
arr["carrot"] = "vegetable";  
  
// Iterate over the properties and elements.  
var s = "";  
for (var key in arr) {  
    s += key + ": " + arr[key];  
    s += "<br />";  
}  
  
document.write (s);  
  
// Output:  
//   0: zero  
//   1: one  
//   2: two  
//   orange: fruit  
//   carrot: vegetable  
```  
  
> [!NOTE]
>  Используйте `Enumerator` объекта для перебора элементов коллекции.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор For](../../javascript/reference/for-statement-javascript.md)   
 [Оператор while](../../javascript/reference/while-statement-javascript.md)