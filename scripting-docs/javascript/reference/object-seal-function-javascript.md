---
title: Функция Object.seal (JavaScript) | Документы Microsoft
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
- Object.seal function
- seal function
ms.assetid: e72c804a-4dab-4ec9-b9df-9c9c908aa12d
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dca9066be9a557b97a52ae749cecfb218504509
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641154"
---
# <a name="objectseal-function-javascript"></a>Функция Object.seal (JavaScript)
Предотвращает изменение атрибутов существующих свойств, а также добавление новых свойств.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
Object.seal(object)  
```  
  
#### <a name="parameters"></a>Параметры  
 `object`  
 Обязательный. Объект, для которого требуется заблокировать атрибуты.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект, который передается в функцию.  
  
## <a name="exceptions"></a>Исключения  
 Если `object` аргумент не является объектом `TypeError` исключения.  
  
## <a name="remarks"></a>Примечания  
 `Object.seal` Функция выполняет следующие:  
  
-   Делает объект нерасширяемым, так что к нему нельзя добавлять новые свойства.  
  
-   Наборы `configurable` атрибут `false` для всех свойств объекта.  
  
 Когда `configurable` атрибут `false`, невозможно изменить атрибуты свойства и не может удалить свойство. Когда `configurable` — `false` и `writable` — `true`, `value` и `writable` атрибуты могут быть изменены.  
  
 `Object.seal` Функции не изменяют `writable` атрибута.  
  
 Дополнительные сведения о настройке свойств атрибутов см. в разделе [функция Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md). Чтобы получить атрибуты свойства, можно использовать [функция Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## <a name="related-functions"></a>Связанные функции  
 Следующие связанные функции предотвратить изменение атрибутов объектов.  
  
|Функция|Сделать объект нерасширяемым|`configurable`имеет значение `false` для каждого свойства|`writable`имеет значение `false` для каждого свойства|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Да|Нет|Нет|  
|`Object.seal`|Да|Да|Нет|  
|[Object.Freeze](../../javascript/reference/object-freeze-function-javascript.md)|Да|Да|Да|  
  
 Следующие функции возвращают `true` Если все условия, которые помечены в таблице ниже.  
  
|Функция|Объект является расширяемым?|`configurable`— `false` для всех свойств?|`writable`— `false` для всех свойств данных?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Да|Нет|Нет|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|Нет|Да|Нет|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Нет|Да|Да|  
  
## <a name="example"></a>Пример  
 В следующем примере показано применение функции `Object.seal`.  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
// Seal the object.  
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
 [Функция Object.Freeze](../../javascript/reference/object-freeze-function-javascript.md)   
 [Функция Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Функция Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)   
 [Функция Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)