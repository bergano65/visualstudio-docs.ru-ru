---
title: Метод Bind (Function) (JavaScript) | Документы Microsoft
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
- parameters [JavaScript], bind method
- arguments [JavaScript], bind method
- bind method [JavaScript]
- this keyword [JavaScript], bind method
ms.assetid: 28946f47-b758-48cf-b508-610a0f2f6e19
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd7fc752df9bd41f8625ac2cb484486dfd19558d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634314"
---
# <a name="bind-method-function-javascript"></a>Метод bind (Function) (JavaScript)
Создает для заданной функции привязанную функцию с тем же телом, что и у исходной функции. В привязанной функции объект `this` разрешается в переданный объект. Привязанная функция имеет определенные исходные параметры.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
function.bind(thisArg[,arg1[,arg2[,argN]]])  
```  
  
#### <a name="parameters"></a>Параметры  
 `function`  
 Обязательный. Объект функции.  
  
 `thisArg`  
 Обязательный. Объект, на который может указывать ключевое слово `this` внутри новой функции.  
  
 `arg1`[,`arg2`[,`argN`]]]  
 Необязательно. Список аргументов, передаваемых новой функции.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Новая функция, аналогичная функции `function`, за исключением объекта `thisArg` и исходных аргументов.  
  
## <a name="exceptions"></a>Исключения  
 Если указанный параметр `function` не является функцией, возникает исключение `TypeError`.  
  
## <a name="example"></a>Пример  
 В следующем примере кода демонстрируется применение метода `bind`.  
  
```JavaScript  
// Define the original function.  
var checkNumericRange = function (value) {  
    if (typeof value !== 'number')  
        return false;  
    else  
        return value >= this.minimum && value <= this.maximum;  
}  
  
// The range object will become the this value in the callback function.  
var range = { minimum: 10, maximum: 20 };  
  
// Bind the checkNumericRange function.  
var boundCheckNumericRange = checkNumericRange.bind(range);  
  
// Use the new function to check whether 12 is in the numeric range.  
var result = boundCheckNumericRange (12);  
document.write(result);  
  
// Output: true  
```  
  
## <a name="example"></a>Пример  
 В следующем примере объект `thisArg` отличается от объекта, который содержит исходный метод.  
  
```JavaScript  
// Create an object that contains the original function.  
var originalObject = {  
    minimum: 50,  
    maximum: 100,  
    checkNumericRange: function (value) {  
        if (typeof value !== 'number')  
            return false;  
        else  
            return value >= this.minimum && value <= this.maximum;  
    }  
}  
  
// Check whether 10 is in the numeric range.  
var result = originalObject.checkNumericRange(10);  
document.write(result + " ");  
// Output: false  
  
// The range object supplies the range for the bound function.  
var range = { minimum: 10, maximum: 20 };  
  
// Create a new version of the checkNumericRange function that uses range.  
var boundObjectWithRange = originalObject.checkNumericRange.bind(range);  
  
// Check whether 10 is in the numeric range.  
var result = boundObjectWithRange(10);  
document.write(result);  
// Output: true  
```  
  
## <a name="example"></a>Пример  
 В следующем коде показано использование аргументов `arg1[,arg2[,argN]]]`. В качестве первого и второго параметра привязанная функция использует параметры, заданные в методе `bind`. В качестве третьего, четвертого и последующих параметров используются параметры, заданные при вызове привязанной функции.  
  
```JavaScript  
// Define the original function with four parameters.  
var displayArgs = function (val1, val2, val3, val4) {  
    document.write(val1 + " " + val2 + " " + val3 + " " + val4);  
}  
  
var emptyObject = {};  
  
// Create a new function that uses the 12 and "a" parameters  
// as the first and second parameters.  
var displayArgs2 = displayArgs.bind(emptyObject, 12, "a");  
  
// Call the new function. The "b" and "c" parameters are used  
// as the third and fourth parameters.  
displayArgs2("b", "c");  
// Output: 12 a b c   
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Объект функции](../../javascript/reference/function-object-javascript.md)   
 [Метод Filter (Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [Использование метода bind](../../javascript/advanced/using-the-bind-method-javascript.md)   
 [Пример приложения Hilo JavaScript (магазин Windows)](http://hilojs.codeplex.com/SourceControl/latest)