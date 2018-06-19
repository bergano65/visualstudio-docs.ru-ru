---
title: Функция Object.Create (JavaScript) | Документы Microsoft
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
- create function [JavaScript]
- Object.create function [JavaScript]
ms.assetid: 0ad31f36-a9ee-444e-b0fe-c87843d03196
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f359908c5c836743e22390580f542df27d7b98e7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640484"
---
# <a name="objectcreate-function-javascript"></a>Функция Object.create (JavaScript)
Создает объект, который имеет указанный прототип и при необходимости, содержащий указанные свойства.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Object.create(prototype, descriptors)  
```  
  
#### <a name="parameters"></a>Параметры  
 `prototype`  
 Обязательный. Объект, используемый в качестве прототипа. Может иметь значение `null`.  
  
 `descriptors`  
 Необязательно. Объект [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] , содержащий один или несколько дескрипторов свойств.  
  
 *Свойство данных* — это свойство, способное получать и задавать значение. Дескриптор свойства данных содержит `value` атрибута, а также `writable`, `enumerable`, и `configurable` атрибуты. Если последние три атрибуты не указаны, они по умолчанию `false`. *Свойства доступа* вызывает определяемую пользователем функцию, каждый раз при получить или задать значение. Дескриптор метода доступа свойства содержит `set` атрибута `get` или оба этих атрибута. Дополнительные сведения см. в разделе [функция Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Новый объект, который имеет указанный внутренний прототип и содержит указанные свойства, если таковые имеются.  
  
## <a name="exceptions"></a>Исключения  
 Объект `TypeError` исключение вызывается, если выполняется хотя бы одно из следующих условий:  
  
-   `prototype` Аргумент не является объектом, не `null`.  
  
-   Дескриптор в `descriptors` аргумент имеет `value` или `writable` , а `get` или `set` атрибута.  
  
-   Дескриптор в `descriptors` аргумент имеет `get` или `set` атрибут, который не является функцией.  
  
## <a name="remarks"></a>Примечания  
 Воспользуйтесь этой функции с помощью `null``prototype` параметр, чтобы остановить цепочки прототипов. Созданный объект будет иметь без прототипа.  
  
## <a name="example"></a>Пример  
 В следующем примере создается объект с помощью `null` прототип и добавляет два перечисляемые свойства.  
  
```JavaScript  
var newObj = Object.create(null, {  
            size: {  
                value: "large",  
                enumerable: true  
            },  
            shape: {  
                value: "round",  
                enumerable: true  
            }  
        });  
  
document.write(newObj.size + "<br/>");  
document.write(newObj.shape + "<br/>");  
document.write(Object.getPrototypeOf(newObj));  
  
// Output:  
// large  
// round  
// null  
  
```  
  
## <a name="example"></a>Пример  
 Следующий пример создает объект, имеющий же внутренний прототип как объект. Можно просмотреть наличие в нем же прототип как объект создан с помощью литерала объекта. [Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md) функция получает прототип для исходного объекта. Чтобы получить дескриптор свойства объекта, можно использовать [функция Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
```JavaScript  
var firstLine = { x: undefined, y: undefined };  
  
var secondLine = Object.create(Object.prototype, {  
        x: {  
                value: undefined,   
                writable: true,   
                configurable: true,   
                enumerable: true  
            },  
            y: {  
                value: undefined,   
                writable: true,   
                configurable: true,   
                enumerable: true  
            }  
});  
  
document.write("first line prototype = " + Object.getPrototypeOf(firstLine));  
document.write("<br/>");  
document.write("second line prototype = " + Object.getPrototypeOf(secondLine));  
  
// Output:  
// first line prototype = [object Object]  
// second line prototype = [object Object]  
```  
  
## <a name="example"></a>Пример  
 Следующий пример создает объект, имеющий же внутренний прототип как объект фигуры.  
  
```JavaScript  
  
// Create the shape object.  
var Shape = { twoDimensional: true, color: undefined, hasLineSegments: undefined };  
  
var Square = Object.create(Object.getPrototypeOf(Shape));  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Функция Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [Метод isPrototypeOf (Object)](../../javascript/reference/isprototypeof-method-object-javascript.md)   
 [Создание объектов](../../javascript/creating-objects-javascript.md)