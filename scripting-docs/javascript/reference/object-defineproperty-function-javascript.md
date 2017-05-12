---
title: "Функция Object.defineProperty (JavaScript) | Microsoft Docs"
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
  - "defineProperty - функция [JavaScript]"
  - "Object.defineProperty - функция [JavaScript]"
ms.assetid: c5d05346-940a-40c2-b12a-e8b25abc8d46
caps.latest.revision: 74
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 74
---
# Функция Object.defineProperty (JavaScript)
Добавляет свойство в объект или изменяет атрибуты существующего свойства.  
  
## Синтаксис  
  
```  
Object.defineProperty(object, propertyname, descriptor)  
```  
  
## Параметры  
 `object`  
 Обязательный.  Объект, для которого нужно добавить или изменить свойство.  Это может быть собственный объект [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] \(встроенный или определяемый пользователем\) или объект DOM.  
  
 `propertyname`  
 Обязательный.  Строка, содержащая имя свойства.  
  
 `descriptor`  
 Обязательный.  Дескриптор свойства.  Это может быть свойство данных или свойство метода доступа.  
  
## Возвращаемое значение  
 Измененный объект.  
  
## Заметки  
 Функцию `Object.defineProperty` можно использовать для выполнения следующих задач:  
  
-   Добавление нового свойства в объект.  Это происходит, если у объекта нет свойства с указанным именем.  
  
-   Изменение атрибутов существующего свойства.  Это происходит, если у объекта уже есть свойство с указанным именем.  
  
 Определение свойства содержится в объекте дескриптора, который описывает атрибуты свойства данных или свойства метода доступа.  Объект дескриптора является параметром функции `Object.defineProperty`.  
  
 Добавить или изменить сразу несколько свойств позволяет [Функция Object.defineProperties](../../javascript/reference/object-defineproperties-function-javascript.md).  
  
## Исключения  
 Исключение `TypeError` возникает при выполнении любого из следующих условий:  
  
-   Аргумент `object` не является объектом.  
  
-   Объект не является [расширяемым](../../javascript/reference/object-isextensible-function-javascript.md), а указанное имя свойства не существует.  
  
-   Параметр `descriptor` имеет атрибут `value` или `writable`, а также `get` или `set`.  
  
-   Параметр `descriptor` имеет атрибут `get` или `set`, который не является функцией или неопределенным.  
  
-   Указанное имя свойства уже существует, существующее свойство имеет атрибут `configurable` со значением `false`, а `descriptor` содержит один или несколько атрибутов, которые отличаются от атрибутов в существующем свойстве.  Однако если существующее свойство имеет атрибут `configurable` со значением `false` и атрибут `writable` со значением `true`, атрибут `value` или `writable` может быть иным.  
  
## Добавление свойства данных  
 В следующем примере функция `Object.defineProperty` добавляет свойство данных в определяемый пользователем объект.  Вместо этого можно добавить свойство в существующий объект DOM. Для этого раскомментируйте строку `var = window.document`.  
  
```javascript  
var newLine = "<br />";  
  
// Create a user-defined object.  
var obj = {};  
  
// Add a data property to the object.  
Object.defineProperty(obj, "newDataProperty", {  
    value: 101,  
    writable: true,  
    enumerable: true,  
    configurable: true  
});  
  
// Set the property value.  
obj.newDataProperty = 102;  
document.write("Property value: " + obj.newDataProperty + newLine);  
  
// Output:  
// Property value: 102  
```  
  
 Чтобы вывести список свойств объекта, добавьте к этому примеру следующий код.  
  
```javascript  
var names = Object.getOwnPropertyNames(obj);  
for (var i = 0; i < names.length; i++) {  
    var prop = names[i];  
  
    document.write(prop + ': ' + obj[prop]);  
    document.write(newLine);  
}  
  
// Output:  
//  newDataProperty: 102  
```  
  
## Изменение свойства данных  
 Чтобы изменить атрибут свойства для объекта, добавьте в представленную выше функцию `addDataProperty` следующий код.  Параметр `descriptor` содержит только атрибут `writable`.  Другие атрибуты свойства данных остаются неизменными.  
  
```javascript  
// Modify the writable attribute of the property.  
Object.defineProperty(obj, "newDataProperty", { writable: false });  
  
// List the property attributes by using a descriptor.  
// Get the descriptor with Object.getOwnPropertyDescriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
for (var prop in descriptor) {  
    document.write(prop + ': ' + descriptor[prop]);  
    document.write(newLine);  
}  
  
// Output  
// writable: false  
// value: 102  
// configurable: true  
// enumerable: true  
```  
  
## Добавление свойства метода доступа  
 В следующем примере функция `Object.defineProperty` добавляет свойство метода доступа в определяемый пользователем объект.  
  
```javascript  
var newLine = "<br />";  
  
// Create a user-defined object.  
var obj = {};  
  
// Add an accessor property to the object.  
Object.defineProperty(obj, "newAccessorProperty", {  
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
});  
  
// Set the property value.  
obj.newAccessorProperty = 30;  
document.write("Property value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// Property value: 30  
  
```  
  
 Чтобы вывести список свойств объекта, добавьте к этому примеру следующий код.  
  
```javascript  
var names = Object.getOwnPropertyNames(obj);  
for (var i = 0; i < names.length; i++) {  
    var prop = names[i];  
  
    document.write(prop + ': ' + obj[prop]);  
    document.write(newLine);  
}  
// Output:  
// in property get accessor  
// newAccessorProperty: 30  
  
```  
  
## Изменение свойства метода доступа  
 Чтобы изменить атрибут свойства для объекта, добавьте следующее в представленный выше код.  Параметр `descriptor` содержит только определение метода доступа `get`.  Другие атрибуты свойства остаются неизменными.  
  
```javascript  
// Modify the get accessor.  
Object.defineProperty(obj, "newAccessorProperty", {  
    get: function () { return this.newaccpropvalue; }  
});  
  
// List the property attributes by using a descriptor.  
// Get the descriptor with Object.getOwnPropertyDescriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newAccessorProperty");  
for (var prop in descriptor) {  
    document.write(prop + ': ' + descriptor[prop]);  
    document.write(newLine);  
}  
  
// Output:  
// get: function () { return this.newaccpropvalue; }  
// set: function (x) { document.write("in property set accessor" + newLine); this.newaccpropvalue = x; }  
// configurable: true  
// enumerable: true  
```  
  
## Изменение свойства для элемента DOM  
 В следующем примере показано, как с помощью функции `Object.getOwnPropertyDescriptor` настраивать встроенные свойства DOM для получения и изменения дескриптора свойства для свойства.  В данном случае код должен содержать элемент DIV с идентификатором div.  
  
```javascript  
// Get the querySelector property descriptor.  
var descriptor = Object.getOwnPropertyDescriptor(Element.prototype, "querySelector");  
  
// Make the property read-only.  
descriptor.value = "query";  
descriptor.writable = false;  
// Apply the changes to the Element prototype.  
Object.defineProperty(Element.prototype, "querySelector", descriptor);  
  
// Get a DOM element from the HTML body.  
var elem = document.getElementById("div");  
  
// Attempt to change the value. This causes the revised value attribute to be called.  
elem.querySelector = "anotherQuery";  
document.write(elem.querySelector);  
  
// Output:  
// query  
  
```  
  
## Требования  
 Internet Explorer 9 \(стандартный режим\), Internet Explorer 10 \(стандартный режим\) и приложения [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] поддерживают все функции.  
  
 [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)] поддерживает объекты DOM, но не поддерживает пользовательские объекты.  Атрибуты `enumerable` и `configurable` могут быть заданы, но не используются.  
  
## См. также  
 [Прототипы модели DOM. Часть 2: поддержка методов доступа](http://msdn.microsoft.com/library/dd229916\(v=VS.85\).aspx)   
 [Функция Object.defineProperties](../../javascript/reference/object-defineproperties-function-javascript.md)   
 [Функция Object.create](../../javascript/reference/object-create-function-javascript.md)   
 [Функция Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Функция Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md)