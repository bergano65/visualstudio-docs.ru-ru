---
title: Функция Object.getOwnPropertyDescriptor (JavaScript) | Документы Microsoft
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
- getOwnPropertyDescriptor method [JavaScript]
ms.assetid: 8f0e1c90-c4f9-44c4-bf76-726bacecbc14
caps.latest.revision: 45
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd147d567fc4d8a39d7a251d55772c40518e7a26
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639034"
---
# <a name="objectgetownpropertydescriptor-function-javascript"></a>Функция Object.getOwnPropertyDescriptor (JavaScript)
Возвращает дескриптор собственного свойства указанного объекта. Дескриптор собственного свойства определяется в самом объекте, а не наследуется от прототипа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Object.getOwnPropertyDescriptor(object, propertyname)  
```  
  
## <a name="parameters"></a>Параметры  
 `object`  
 Обязательный. Объект, содержащий свойство.  
  
 `propertyname`  
 Обязательный. Имя свойства.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Дескриптор свойства.  
  
## <a name="remarks"></a>Примечания  
 Функция `Object.getOwnPropertyDescriptor` позволяет получить объект дескриптора, описывающий атрибуты свойства.  
  
 [Функция Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md) используется для добавления или изменения свойств.  
  
## <a name="data-property-example"></a>Пример свойства данных  
 Код в следующем примере возвращает дескриптор свойства данных и использует его, чтобы сделать свойство доступным только для чтения.  
  
```JavaScript  
// Create a user-defined object.  
var obj = {};  
  
// Add a data property.  
obj.newDataProperty = "abc";  
  
// Get the property descriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
  
// Change a property attribute.  
descriptor.writable = false;  
Object.defineProperty(obj, "newDataProperty", descriptor);  
  
```  
  
 Чтобы вывести список атрибутов свойства, добавьте к примеру следующий код.  
  
```JavaScript  
// Get the descriptor from the object.  
var desc2 = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
  
// List the descriptor attributes.  
for (var prop in desc2) {  
    document.write(prop + ': ' + desc2[prop]);  
    document.write("<br />");  
}  
  
// Output:  
// value: abc  
// writable: false  
// enumerable: true  
// configurable: true  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] поддерживает все функции.  
  
 [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)] поддерживает объекты DOM, но не поддерживает пользовательские объекты. Атрибуты `enumerable` и `configurable` можно указать, но они не используются.  
  
## <a name="see-also"></a>См. также  
 [Прототипы модели DOM., часть 2: Поддержка методов доступа (getter)](http://msdn.microsoft.com/library/dd229916\(v=VS.85\).aspx)   
 [Функция Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md)