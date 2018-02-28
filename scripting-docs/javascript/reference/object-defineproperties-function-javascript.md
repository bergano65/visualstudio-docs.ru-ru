---
title: "Функция Object.defineProperties (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Object.defineProperties function [JavaScript]
ms.assetid: 2dae6658-a1c9-495f-bf06-bb3e964e6762
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 65f4f5817a105283a26c971bd98869d000ca0bc2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="objectdefineproperties-function-javascript"></a>Функция Object.defineProperties (JavaScript)
Добавляет одно или несколько свойств в объект и изменяет атрибуты существующих свойств.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.defineProperties(object, descriptors)  
```  
  
## <a name="parameters"></a>Параметры  
 `object`  
 Обязательный. Объект, для которого требуется добавить или изменить свойства. Это может быть собственный [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] объект или объект DOM.  
  
 `descriptors`  
 Обязательный. Объект [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] , содержащий один или несколько объектов дескриптора. Каждый объект дескриптора описывает свойства данных или свойства метода доступа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект, который был передан в функцию.  
  
## <a name="remarks"></a>Примечания  
 `descriptors` Аргумент представляет собой объект, содержащий один или несколько объектов дескриптора.  
  
 Объект *свойство данных* свойство, которое можно сохранять и извлекать значения. Дескриптор свойства данных содержит `value` атрибута `writable` или оба этих атрибута. Дополнительные сведения см. в разделе [свойства данных и методов доступа](../../javascript/advanced/data-properties-and-accessor-properties.md).  
  
 *Свойства доступа* вызывает определяемую пользователем функцию, каждый раз при задать или получить значение свойства. Дескриптор метода доступа свойства содержит `set` атрибута `get` или оба этих атрибута.  
  
 Если объект уже имеет свойство с указанным именем, изменяются атрибуты свойства. Дополнительные сведения см. в разделе [функция Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
 Для создания объекта и добавлять свойства к новому объекту, можно использовать [функция Object.create](../../javascript/reference/object-create-function-javascript.md).  
  
## <a name="adding-properties"></a>Добавление свойств  
 В следующем примере `Object.defineProperties` функция добавляет свойство данных и свойства метода доступа в определяемый пользователем объект.  
  
 В примере литерала объекта, для создания `descriptors` объекта с `newDataProperty` и `newAccessorProperty` объекты дескрипторов.  
  
```JavaScript  
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
  
 Как и предыдущий пример в следующем примере добавляется свойства динамически вместо с литерала объекта.  
  
```JavaScript  
  
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
  
## <a name="modifying-properties"></a>Изменение свойств  
 Чтобы изменить атрибуты свойства для объекта, добавьте следующий код. `Object.defineProperties` Функция изменяет `writable` атрибут `newDataProperty`и изменяет `enumerable` атрибут `newAccessorProperty`. Он добавляет `anotherDataProperty` объекту, так как это имя свойства уже существует.  
  
```  
Object.defineProperties(obj, {  
    newDataProperty: { writable: false },  
    newAccessorProperty: { enumerable: false },  
    anotherDataProperty: { value: "abc" }  
});  
```  
  
## <a name="requirements"></a>Требования  
 Поддерживаемые стандарты стандартов Internet Explorer 10, Internet Explorer 9 и [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] приложения. Поддерживается в Internet Explorer 8 для объектов модели DOM, в противном случае не поддерживается.  
  
## <a name="see-also"></a>См. также  
 [Функция Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Функция Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md)   
 [Функция Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Функция Object.CREATE](../../javascript/reference/object-create-function-javascript.md)   
 [Объект Object](../../javascript/reference/object-object-javascript.md)