---
title: Функция Object.defineProperty (JavaScript) | Документы Microsoft
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
- defineProperty function [JavaScript]
- Object.defineProperty function [JavaScript]
ms.assetid: c5d05346-940a-40c2-b12a-e8b25abc8d46
caps.latest.revision: 74
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 89291f5c836f74a5dd71099328ce389a12f6fd24
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24642124"
---
# <a name="objectdefineproperty-function-javascript"></a>Функция Object.defineProperty (JavaScript)
Добавляет свойство в объект или изменяет атрибуты существующего свойства.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Object.defineProperty(object, propertyname, descriptor)  
```  
  
## <a name="parameters"></a>Параметры  
 `object`  
 Обязательный. Объект, для которого нужно добавить или изменить свойство. Это может быть собственный объект [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] (встроенный или определяемый пользователем) или объект DOM.  
  
 `propertyname`  
 Обязательный. Строка, содержащая имя свойства.  
  
 `descriptor`  
 Обязательный. Дескриптор свойства. Это может быть свойство данных или свойство метода доступа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Измененный объект.  
  
## <a name="remarks"></a>Примечания  
 Функцию `Object.defineProperty` можно использовать для выполнения следующих задач:  
  
-   Добавление нового свойства в объект. Это происходит, если у объекта нет свойства с указанным именем.  
  
-   Изменение атрибутов существующего свойства. Это происходит, если у объекта уже есть свойство с указанным именем.  
  
 Определение свойства содержится в объекте дескриптора, который описывает атрибуты свойства данных или свойства метода доступа. Объект дескриптора является параметром функции `Object.defineProperty`.  
  
 Для добавления нескольких свойств к объекту или изменить несколько существующих свойств, можно использовать [функция Object.defineProperties](../../javascript/reference/object-defineproperties-function-javascript.md).  
  
## <a name="exceptions"></a>Исключения  
 Исключение `TypeError` возникает при выполнении любого из следующих условий:  
  
-   Аргумент `object` не является объектом.  
  
-   Объект не является [расширяемый](../../javascript/reference/object-isextensible-function-javascript.md) и указанное имя свойства не существует...  
  
-   Параметр `descriptor` имеет атрибут `value` или `writable`, а также `get` или `set`.  
  
-   Параметр `descriptor` имеет атрибут `get` или `set`, который не является функцией или неопределенным.  
  
-   Указанное имя свойства уже существует, существующее свойство имеет атрибут `configurable` со значением `false`, а `descriptor` содержит один или несколько атрибутов, которые отличаются от атрибутов в существующем свойстве. Однако если существующее свойство имеет атрибут `configurable` со значением `false` и атрибут `writable` со значением `true`, атрибут `value` или `writable` может быть иным.  
  
## <a name="adding-a-data-property"></a>Добавление свойства данных  
 В следующем примере функция `Object.defineProperty` добавляет свойство данных в определяемый пользователем объект. Вместо этого можно добавить свойство в существующий объект DOM. Для этого раскомментируйте строку `var = window.document`.  
  
```JavaScript  
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
  
```JavaScript  
var names = Object.getOwnPropertyNames(obj);  
for (var i = 0; i < names.length; i++) {  
    var prop = names[i];  
  
    document.write(prop + ': ' + obj[prop]);  
    document.write(newLine);  
}  
  
// Output:  
//  newDataProperty: 102  
```  
  
## <a name="modifying-a-data-property"></a>Изменение свойства данных  
 Чтобы изменить атрибут свойства для объекта, добавьте в представленную выше функцию `addDataProperty` следующий код. Параметр `descriptor` содержит только атрибут `writable`. Другие атрибуты свойства данных остаются неизменными.  
  
```JavaScript  
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
  
## <a name="adding-an-accessor-property"></a>Добавление свойства метода доступа  
 В следующем примере функция `Object.defineProperty` добавляет свойство метода доступа в определяемый пользователем объект.  
  
```JavaScript  
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
  
```JavaScript  
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
  
## <a name="modifying-an-accessor-property"></a>Изменение свойства метода доступа  
 Чтобы изменить атрибут свойства для объекта, добавьте следующее в представленный выше код. Параметр `descriptor` содержит только определение метода доступа `get`. Другие атрибуты свойства остаются неизменными.  
  
```JavaScript  
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
  
## <a name="modifying-a-property-on-a-dom-element"></a>Изменение свойства для элемента DOM  
 В следующем примере показано, как с помощью функции `Object.getOwnPropertyDescriptor` настраивать встроенные свойства DOM для получения и изменения дескриптора свойства для свойства. В данном случае код должен содержать элемент DIV с идентификатором div.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Требования  
 Internet Explorer 9 (стандартный режим), Internet Explorer 10 (стандартный режим) и приложения [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] поддерживают все функции.  
  
 [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)] поддерживает объекты DOM, но не поддерживает пользовательские объекты. Атрибуты `enumerable` и `configurable` можно указать, но они не используются.  
  
## <a name="see-also"></a>См. также  
 [Прототипы модели DOM., часть 2: Поддержка методов доступа (getter)](http://msdn.microsoft.com/library/dd229916\(v=VS.85\).aspx)   
 [Функция Object.defineProperties](../../javascript/reference/object-defineproperties-function-javascript.md)   
 [Функция Object.CREATE](../../javascript/reference/object-create-function-javascript.md)   
 [Функция Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Функция Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md)