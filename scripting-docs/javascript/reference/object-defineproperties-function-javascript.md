---
title: "Функция Object.defineProperties (JavaScript) | Microsoft Docs"
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
  - "Object.defineProperties - функция [JavaScript]"
ms.assetid: 2dae6658-a1c9-495f-bf06-bb3e964e6762
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# Функция Object.defineProperties (JavaScript)
Добавляет одно или несколько свойств к объекту, и\/или изменяет атрибуты имеющихся свойств.  
  
## Синтаксис  
  
```  
  
object.defineProperties(object, descriptors)  
```  
  
## Параметры  
 `object`  
 Обязательный параметр.  Объект, для которого добавляется или изменяется свойства.  Это может быть собственным объектом [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] или объектом DOM.  
  
 `descriptors`  
 Обязательный параметр.  Объект [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], содержащий один или несколько объектов дескриптора.  Каждый объект дескриптора описывает свойство данных или свойство доступа.  
  
## Возвращаемое значение  
 Объект, переданный функции.  
  
## Заметки  
 Аргумент `descriptors` представляет собой объект, содержащий один или несколько объектов дескриптора.  
  
 *Свойство данных* — это свойство, которое может хранить и извлекать значения.  Дескриптор свойства данных содержит атрибут `value`, атрибут `writable` или их обоих.  Для получения дополнительной информации см. [Свойства данных и свойства доступа](../../javascript/advanced/data-properties-and-accessor-properties.md).  
  
 *Свойство доступа* вызывает предоставленную пользователем функцию каждый раз, когда происходит установка или извлечение значения свойства.  Дескриптор свойства доступа содержит атрибут `set`, атрибут `get` или их обоих.  
  
 Если объект уже имеет свойство с указанными именем, то атрибуты свойства изменяются.  Для получения дополнительной информации см. [Функция Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
 Для создания объекта и добавления свойств к новому объекту можно использовать [Функция Object.create](../../javascript/reference/object-create-function-javascript.md).  
  
## Добавление свойств  
 В следующем примере функция `Object.defineProperties` добавляет свойство данных и свойство доступа к определяемому пользователем объекту.  
  
 В примере используется литерал объекта для создания объекта `descriptors` с объектами дескриптора `newDataProperty` и `newAccessorProperty`.  
  
```javascript  
var newLine = "<br />";  
  
var obj = {};  
Object.defineProperties(obj, {  
    newDataProperty: {  
        value: 101,  
        writable: true,  
        enumerable: true,  
        configurable: true  
    },  
    newAccessorProperty: {  
        set: function (x) {  
            document.write("in property set accessor" + newLine);  
            this.newaccpropvalue = x;  
        },  
        get: function () {  
            document.write("in property get accessor" + newLine);  
            return this.newaccpropvalue;  
        },  
        enumerable: true,  
        configurable: true  
    }});  
  
// Set the accessor property value.  
obj.newAccessorProperty = 10;  
document.write ("newAccessorProperty value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// newAccessorProperty value: 10  
  
```  
  
 Как и в предыдущем примере, в следующем примере показано динамическое добавление свойства вместо добавления с литералом объекта.  
  
```javascript  
  
var newLine = "<br />";  
  
// Create the descriptors object.  
var descriptors = new Object();  
  
// Add a data property descriptor to the descriptors object.  
descriptors.newDataProperty = new Object();  
descriptors.newDataProperty.value = 101;  
descriptors.newDataProperty.writable = true;  
descriptors.newDataProperty.enumerable = true;  
descriptors.newDataProperty.configurable = true;  
  
// Add an accessor property descriptor to the descriptors object.  
descriptors.newAccessorProperty = new Object();  
descriptors.newAccessorProperty.set = function (x) {  
    document.write("in property set accessor" + newLine);  
    this.newaccpropvalue = x;  
};  
descriptors.newAccessorProperty.get = function () {  
    document.write("in property get accessor" + newLine);  
    return this.newaccpropvalue;  
};  
descriptors.newAccessorProperty.enumerable = true;  
descriptors.newAccessorProperty.configurable = true;  
  
// Call the Object.defineProperties function.  
var obj = new Object();  
Object.defineProperties(obj, descriptors);  
  
// Set the accessor property value.  
obj.newAccessorProperty = 10;  
document.write ("newAccessorProperty value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// newAccessorProperty value: 10  
  
```  
  
## Изменение свойств  
 Чтобы изменить атрибуты свойства для объекта, добавьте следующий код.  Функция `Object.defineProperties` изменяет атрибут `writable` объекта дескриптора `newDataProperty` и атрибут `enumerable` объекта дескриптора `newAccessorProperty`.  Она добавляет `anotherDataProperty` к объекту, поскольку это имя свойства еще не существует.  
  
```  
Object.defineProperties(obj, {  
    newDataProperty: { writable: false },  
    newAccessorProperty: { enumerable: false },  
    anotherDataProperty: { value: "abc" }  
});  
```  
  
## Требования  
 Поддерживается в стандартах Internet Explorer 9, стандартах Internet Explorer 10 и приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  Поддерживается в Internet Explorer 8 только для объектов DOM, для других объектов не поддерживается.  
  
## См. также  
 [Функция Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Функция Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md)   
 [Функция Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Функция Object.create](../../javascript/reference/object-create-function-javascript.md)   
 [Объект Object](../../javascript/reference/object-object-javascript.md)