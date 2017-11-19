---
title: "Функция Object.isSealed (JavaScript) | Документы Microsoft"
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
- properties [JavaScript], locking attributes
- isSealed function [JavaScript]
- Object.isSealed [JavaScript]
ms.assetid: af4f192e-cebe-44b9-8eef-90c096f5ae8f
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d3b9cb603a456382e3b23e6f7d0037063027b98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="objectissealed-function-javascript"></a>Функция Object.isSealed (JavaScript)
Возвращает значение `true`, если объект не допускает изменение существующих атрибутов свойств, а также добавление новых свойств.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
Object.isSealed(object)  
```  
  
#### <a name="parameters"></a>Параметры  
 `object`  
 Обязательный. Объект для тестирования.  
  
## <a name="return-value"></a>Возвращаемое значение  
 `true`Если выполняются оба следующих условия:  
  
-   Объект нерасширяемым, указывающая, что нельзя добавить новые свойства в объект.  
  
-   `configurable` Атрибут `false` для всех существующих свойств.  
  
 Если объект не имеет все свойства, функция возвращает `true` , если объект нерасширяемым.  
  
## <a name="exceptions"></a>Исключения  
 Если `object` аргумент не является объектом `TypeError` исключения.  
  
## <a name="remarks"></a>Примечания  
 Когда `configurable` атрибут свойства `false`, нельзя изменить атрибуты свойств, а не удается удалить свойство. Когда `writable` — `false`, значение свойства не может изменяться. Когда `configurable` — `false` и `writable` — `true`, `value` и `writable` атрибуты могут быть изменены.  
  
 `Object.isSealed` Функция не использует `writable` атрибут свойства для определения возвращаемого значения.  
  
 Сведения о настройке свойств атрибутов см. в разделе [функция Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md). Для получения атрибутов свойства, можно использовать [функция Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## <a name="related-functions"></a>Связанные функции  
 Следующие связанные функции предотвратить изменение атрибутов объектов.  
  
|Функция|Сделать объект нерасширяемым|`configurable`имеет значение `false` для каждого свойства|`writable`имеет значение `false` для каждого свойства|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Да|Нет|Нет|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|Да|Да|Нет|  
|[Object.Freeze](../../javascript/reference/object-freeze-function-javascript.md)|Да|Да|Да|  
  
 Следующие функции возвращают `true` Если все условия, которые помечены в таблице ниже.  
  
|Функция|Объект является расширяемым?|`configurable`— `false` для всех свойств?|`writable`— `false` для всех свойств данных?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Да|Нет|Нет|  
|`Object.isSealed`|Нет|Да|Нет|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Нет|Да|Да|  
  
## <a name="example"></a>Пример  
 В следующем примере показано применение функции `Object.isSealed`.  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Seal the object, and verify that it is sealed.  
Object.seal(obj);  
document.write(Object.isSealed(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.   
obj.newProp = 50;  
document.write(obj.newProp);  
document.write("<br/>");  
  
// Try to delete a property, and then verify that it is still present.   
delete obj.length;  
document.write(obj.length);  
  
// Output:  
// true  
// undefined  
// 10  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Функция Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Функция Object.seal](../../javascript/reference/object-seal-function-javascript.md)   
 [Функция Object.Freeze](../../javascript/reference/object-freeze-function-javascript.md)   
 [Функция Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Функция Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)   
 [Функция Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Функция Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)