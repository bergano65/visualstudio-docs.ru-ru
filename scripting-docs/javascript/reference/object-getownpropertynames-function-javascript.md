---
title: "Функция Object.getOwnPropertyNames (JavaScript) | Microsoft Docs"
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
  - "getOwnPropertyNames - метод [JavaScript]"
  - "Object.getOwnPropertyNames - метод [JavaScript]"
ms.assetid: 59f4b6b1-02be-44b3-a06c-a5ca8f70c3d8
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Функция Object.getOwnPropertyNames (JavaScript)
Возвращает имена собственных свойств объекта.  Собственные свойства объекта — те, которые определены непосредственно для этого объекта, а не унаследованы от прототипа объекта.  Свойства объекта включают как поля \(объекты\), так и функции.  
  
## Синтаксис  
  
```javascript  
Object.getOwnPropertyNames(object)  
```  
  
#### Параметры  
  
|Параметр|Определение|  
|--------------|-----------------|  
|`object`|Обязательный.  Объект, содержащий собственные свойства.|  
  
## Возвращаемое значение  
 Массив, содержащий имена собственных свойств объекта.  
  
## Исключения  
 Если значение, заданное для аргумента `object` не является именем объекта, возникает исключение `TypeError`.  
  
## Заметки  
 Метод `getOwnPropertyNames` возвращает имена как перечислимых, так и неперечислимых свойств и методов.  Чтобы вернуть имена только перечислимых свойств и методов, можно использовать [Функция Object.keys](../../javascript/reference/object-keys-function-javascript.md).  
  
## Пример  
 В следующем примере создается объект, имеющий три свойства и метод.  Затем используется метод `getOwnPropertyNames` для получения собственных свойств \(включая метод\) объекта.  
  
```javascript  
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
  
## Пример  
 В следующем примере отображаются имена свойств, начинающиеся с буквы "s" объекта spaghetti, созданного с помощью конструктора Pasta.  
  
```javascript  
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
  
## Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## См. также  
 [Функция Object.keys](../../javascript/reference/object-keys-function-javascript.md)