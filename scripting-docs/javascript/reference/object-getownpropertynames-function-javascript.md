---
title: "Функция Object.getOwnPropertyNames (JavaScript) | Документы Microsoft"
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
- getOwnPropertyNames method [JavaScript]
- Object.getOwnPropertyNames method [JavaScript]
ms.assetid: 59f4b6b1-02be-44b3-a06c-a5ca8f70c3d8
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76ca0036b9dedf7b4cee7b543469939e35dfe8d1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="objectgetownpropertynames-function-javascript"></a>Функция Object.getOwnPropertyNames (JavaScript)
Возвращает имена собственные свойства объекта. Собственные свойства объекта являются те, которые определены в этом объекте и не наследуется от прототипа. Свойства объекта включают поля (объекты) и функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
Object.getOwnPropertyNames(object)  
```  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Определение|  
|---------------|----------------|  
|`object`|Обязательный. Объект, содержащий собственные свойства.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Массив, содержащий имена собственные свойства объекта.  
  
## <a name="exceptions"></a>Исключения  
 Если значение указано для `object` аргумент не является именем объекта, `TypeError` исключения.  
  
## <a name="remarks"></a>Примечания  
 `getOwnPropertyNames` Метод возвращает имена перечисляемую и не перечисляемых свойств и методов. Чтобы вернуть только имена перечисляемые свойства и методы, можно использовать [функция Object.keys](../../javascript/reference/object-keys-function-javascript.md).  
  
## <a name="example"></a>Пример  
 Следующий пример создает объект, который имеет три свойств и методов. Затем он использует `getOwnPropertyNames` метод, чтобы получить собственные свойства (включая метод) объекта.  
  
```JavaScript  
function Pasta(grain, width, shape) {  
    // Define properties.  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Get the own property names.  
var arr = Object.getOwnPropertyNames(spaghetti);  
document.write (arr);  
  
// Output:  
//   grain,width,shape,toString  
```  
  
## <a name="example"></a>Пример  
 В следующем примере отображаются имена свойств, которые начинаются на букву "в **спагетти** объект создан с **Макарон** конструктор.  
  
```JavaScript  
function Pasta(grain, size, shape) {  
    this.grain = grain;   
    this.size = size;   
    this.shape = shape;   
}  
  
var spaghetti = new Pasta("wheat", 2, "circle");  
  
var names = Object.getOwnPropertyNames(spaghetti).filter(CheckKey);  
document.write(names);   
  
// Check whether the first character of a string is 's'.   
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);   
    if (firstChar.toLowerCase() == 's')  
        return true;   
    else  
         return false;   
}  
// Output:  
// size,shape  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Функция Object.keys](../../javascript/reference/object-keys-function-javascript.md)