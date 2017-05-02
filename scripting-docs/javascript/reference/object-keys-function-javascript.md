---
title: "Функция Object.keys (JavaScript) | Microsoft Docs"
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
  - "keys - метод [JavaScript]"
  - "Object.keys - метод [JavaScript]"
ms.assetid: cf4a7daf-cf28-4467-bc6b-f7f106ec3876
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Функция Object.keys (JavaScript)
Возвращает имена перечислимых свойств и методов объекта.  
  
## Синтаксис  
  
```javascript  
Object.keys(object)  
```  
  
#### Параметры  
  
|Параметр|Определение|  
|--------------|-----------------|  
|`object`|Обязательный.  Объект, содержащий все свойства и методы.  Это может быть объект, созданный пользователем, или существующий объект DOM.|  
  
## Возвращаемое значение  
 Массив, содержащий имена перечислимых свойства и методов объекта.  
  
## Исключения  
 Если значение, заданное для аргумента `object` не является именем объекта, возникает исключение `TypeError`.  
  
## Заметки  
 Метод `keys` возвращает имена только перечислимых свойств и методов.  Для возвращения имен как перечислимых, так и неперечислимых свойств и методов можно использовать [Функция Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md).  
  
 Дополнительные сведения о свойстве `enumerable` см. в разделах [Функция Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md) и [Функция Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## Пример  
 В следующем примере создается объект, имеющий три свойства и метод.  Затем используется метод `keys` для получения свойств и методов объекта.  
  
```javascript  
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
  
## Пример  
 В следующем примере отображаются имена всех перечислимых свойств объекта Pasta, начинающихся с буквы "g".  
  
```javascript  
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
  
## Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## См. также  
 [Функция Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md)