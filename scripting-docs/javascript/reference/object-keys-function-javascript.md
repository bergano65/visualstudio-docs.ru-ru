---
title: "Функция Object.Keys (JavaScript) | Документы Microsoft"
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
- Object.keys method [JavaScript]
- keys method [JavaScript]
ms.assetid: cf4a7daf-cf28-4467-bc6b-f7f106ec3876
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0e725c3ab7206b04d9a900cb614b57c37dfc4351
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="objectkeys-function-javascript"></a>Функция Object.keys (JavaScript)
Возвращает имена перечисляемых свойств и методов объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
Object.keys(object)  
```  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Определение|  
|---------------|----------------|  
|`object`|Обязательный. Объект, содержащий свойства и методы. Это может быть объект, который был создан, либо существующий объект объектной модели документа (DOM).|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Массив, содержащий имена перечисляемых свойств и методов объекта.  
  
## <a name="exceptions"></a>Исключения  
 Если значение указано для `object` аргумент не является именем объекта, `TypeError` исключения.  
  
## <a name="remarks"></a>Примечания  
 `keys` Метод возвращает только имена перечисляемые свойства и методы. Для возврата имен перечисляемую и не перечисляемых свойств и методов, можно использовать [функция Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md).  
  
 Сведения о `enumerable` атрибута свойства. в разделе [функция Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md) и [функция Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## <a name="example"></a>Пример  
 Следующий пример создает объект, который имеет три свойств и методов. Затем он использует `keys` метод получения свойства и методы объекта.  
  
```JavaScript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
  
    // Define a method.  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Put the enumerable properties and methods of the object in an array.  
var arr = Object.keys(spaghetti);  
document.write (arr);  
  
// Output:  
// grain,width,shape,toString  
```  
  
## <a name="example"></a>Пример  
 Следующий пример отображает имена всех перечисляемые свойства, которые начинаются с буквы «g» в объекте Макарон.  
  
```JavaScript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
}  
  
var polenta = new Pasta("corn", 1, "mush");  
  
var keys = Object.keys(polenta).filter(CheckKey);  
document.write(keys);  
  
// Check whether the first character of a string is "g".  
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);  
    if (firstChar.toLowerCase() == "g")  
        return true;  
    else  
        return false;  
}  
  
// Output:  
// grain  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Функция Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md)