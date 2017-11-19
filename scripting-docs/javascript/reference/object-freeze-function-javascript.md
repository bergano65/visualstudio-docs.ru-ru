---
title: "Функция Object.Freeze (JavaScript) | Документы Microsoft"
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
- Object.freeze function
- freeze function
ms.assetid: 83ffe193-0a37-4e0c-9b66-44c422765fb3
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec08b34c3c8b32245928e6e75f5df1fbdfe2d4a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="objectfreeze-function-javascript"></a>Функция Object.freeze (JavaScript)
Предотвращает изменение существующих атрибутов и значений свойств, а также добавление новых свойств.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
Object.freeze(object)  
```  
  
#### <a name="parameters"></a>Параметры  
 `object`  
 Обязательный. Объект, для которого требуется заблокировать атрибуты.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект, который передается в функцию.  
  
## <a name="exceptions"></a>Исключения  
 Если `object` аргумент не является объектом `TypeError` исключения.  
  
## <a name="remarks"></a>Примечания  
 `Object.freeze` Функция выполняет следующее:  
  
-   Делает объект нерасширяемым, так что к нему нельзя добавлять новые свойства.  
  
-   Наборы `configurable` атрибут `false` для всех свойств объекта. Когда `configurable` является `false`, невозможно изменить атрибуты свойства и не может удалить свойство.  
  
-   Наборы `writable` атрибут `false` для всех свойств объекта данных. Когда `writable` имеет значение false, значение свойства не может изменяться.  
  
 Дополнительные сведения о настройке свойств атрибутов см. в разделе [функция Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md). Для получения атрибутов свойства, можно использовать [функция Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## <a name="related-functions"></a>Связанные функции  
 Следующие связанные функции предотвратить изменение атрибутов объектов.  
  
|Функция|Сделать объект нерасширяемым|`configurable`имеет значение `false` для каждого свойства|`writable`имеет значение `false` для каждого свойства|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Да|Нет|Нет|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|Да|Да|Нет|  
|`Object.freeze`|Да|Да|Да|  
  
 Следующие функции возвращают `true` Если все условия, которые помечены в таблице ниже.  
  
|Функция|Объект является расширяемым?|`configurable`— `false` для всех свойств?|`writable`— `false` для всех свойств данных?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Да|Нет|Нет|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|Нет|Да|Да|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Нет|Да|Да|  
  
## <a name="example"></a>Пример  
 В следующем примере показано применение функции `Object.freeze`.  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Freeze the object.  
Object.freeze(obj);  
  
// Try to add a new property, and then verify that it is not added.   
    obj.newProp = 50;  
    document.write(obj.newProp);  
    document.write("<br/>");  
  
// Try to delete a property, and then verify that it is still present.   
delete obj.length;  
document.write(obj.length);  
document.write("<br/>");  
  
// Try to change a property value, and then verify that it is not changed.   
obj.pasta = "linguini";  
document.write(obj.pasta);  
  
// Output:  
// undefined  
// 10  
// spaghetti  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Функция Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Функция Object.seal](../../javascript/reference/object-seal-function-javascript.md)   
 [Функция Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Функция Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)   
 [Функция Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)