---
title: "Функция Object.preventExtensions (JavaScript) | Документы Microsoft"
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
- properties [JavaScript], preventing new
- preventing new properties [JavaScript]
- preventExtensions function [JavaScript]
- Object.preventExtensions function [JavaScript]
ms.assetid: e6b48197-2374-4437-a9fe-519dd45a2077
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 868f917cc2249a1634194e4b2dd097e0dcbd4c08
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="objectpreventextensions-function-javascript"></a>Функция Object.preventExtensions (JavaScript)
Предотвращает добавление новых свойств к объекту.  
  
## <a name="syntax"></a>Синтаксис  
  
```JavaScript  
Object.preventExtensions(object)  
```  
  
#### <a name="parameters"></a>Параметры  
 `object`  
 Обязательный. Объект, который необходимо сделать нерасширяемым.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект, который передается в функцию.  
  
## <a name="exceptions"></a>Исключения  
 Если `object` аргумент не является объектом `TypeError` исключения.  
  
## <a name="remarks"></a>Примечания  
 `Object.preventExtensions` Функция делает объект нерасширяемым, для новых именованных свойств нельзя добавить к нему. После внесения объект нерасширяемым, его нельзя сделать расширяемые.  
  
 Сведения о настройке свойств атрибутов см. в разделе [функция Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
## <a name="related-functions"></a>Связанные функции  
 Следующие связанные функции предотвратить изменение атрибутов объектов.  
  
|Функция|Сделать объект нерасширяемым|`configurable`имеет значение `false` для каждого свойства|`writable`имеет значение `false` для каждого свойства|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|`Object.preventExtensions`|Да|Нет|Нет|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|Да|Да|Нет|  
|[Object.Freeze](../../javascript/reference/object-freeze-function-javascript.md)|Да|Да|Да|  
  
 Следующие функции возвращают `true` Если все условия, которые помечены в таблице ниже.  
  
|Функция|Объект является расширяемым?|`configurable`— `false` для всех свойств?|`writable`— `false` для всех свойств данных?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Да|Нет|Нет|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|Нет|Да|Нет|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Нет|Да|Да|  
  
## <a name="example"></a>Пример  
 В следующем примере показано применение функции `Object.preventExtensions`.  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Make the object non-extensible.  
Object.preventExtensions(obj);  
document.write(Object.isExtensible(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.  
obj.newProp = 50;  
document.write(obj.newProp);  
  
// Output:  
// false  
// undefined  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Функция Object.seal](../../javascript/reference/object-seal-function-javascript.md)   
 [Функция Object.Freeze](../../javascript/reference/object-freeze-function-javascript.md)   
 [Функция Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Функция Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)   
 [Функция Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)