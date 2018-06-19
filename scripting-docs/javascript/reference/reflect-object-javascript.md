---
title: Объект reflect (JavaScript) | Документы Microsoft
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
ms.assetid: 1df74f34-2eb4-42f1-a930-b943c86daa0e
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3574c54ee7ff69f56951cd7f4c9a93cac5275fc1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640924"
---
# <a name="reflect-object-javascript"></a>Объект Reflect (JavaScript)
Предоставляет методы для использования в перехватываемых операциях.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Reflect.[method]  
```  
  
#### <a name="parameters"></a>Параметры  
 `method`  
 Обязательный. Имя одного из методов объекта `Reflect`.  
  
## <a name="remarks"></a>Примечания  
 Создать экземпляр объекта Reflect с помощью оператора `new` нельзя.  
  
 Методы reflect часто используются с [учетные записи-посредники](../../javascript/reference/proxy-object-javascript.md) так, как они позволяют делегировать поведение по умолчанию без реализации по умолчанию в коде.  
  
 Объект Reflect предоставляет статический метод с тем же именем, что и у каждого прокси-исключения. Описания в таблице не являются исчерпывающими.  
  
|Метод|Описание|  
|------------|-----------------|  
|`Reflect.apply(target, thisArg, args)`|Аналогично [применить](../../javascript/reference/apply-method-function-javascript.md) метод объекта функции.|  
|`Reflect.construct(target, args)`|Функция, эквивалентная оператору `new`.|  
|`Reflect.defineProperty(target, propertyName, descriptor)`|Аналогично [Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md). Возвращает логическое значение, указывающее, успешно ли выполнен вызов.|  
|`Reflect.deleteProperty(target, propertyName)`|Аналог оператора `delete`. Возвращает логическое значение, указывающее, успешно ли выполнен вызов.|  
|`Reflect.enumerate(target)`|Аналогично [for... в](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md) инструкции [Object.getOwnPropertySymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md), [Object.keys](../../javascript/reference/object-keys-function-javascript.md) функции, и [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md).|  
|`Reflect.get(target, propertyName, receiver)`|Функция, эквивалентная любому [считывания](../../javascript/creating-objects-javascript.md) свойства.|  
|`Reflect.getOwnPropertyDescriptor(target, propertyName)`|Аналогично [Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md). Возвращает логическое значение, указывающее, успешно ли выполнен вызов.|  
|`Reflect.getPrototypeOf(target)`|Аналогично [Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md).|  
|`Reflect.has(target, propertyName)`|Аналогично `in` оператор, [метод hasOwnProperty (Object)](../../javascript/reference/hasownproperty-method-object-javascript.md), а также другие методы. Возвращает логическое значение, указывающее, успешно ли выполнен вызов.|  
|`Reflect.isExtensible(target)`|Аналогично [Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md).|  
|`Reflect.ownKeys(target)`|Аналогично [Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md).|  
|`Reflect.preventExtensions(target)`|Аналогично [Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md). Возвращает логическое значение, указывающее, успешно ли выполнен вызов.|  
|`Reflect.set(target, propertyName, value, receiver)`|Аналог применения любого [setter](../../javascript/creating-objects-javascript.md) свойство. Возвращает логическое значение, указывающее, успешно ли выполнен вызов.|  
|`Reflect.setPrototypeOf(target, prototype)`|Аналогично [Object.setPrototypeOf](../../javascript/reference/object-setprototypeof-function-javascript.md). Возвращает логическое значение, указывающее, успешно ли выполнен вызов.|  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано, как использовать `Reflect.get` для записи прокси-элемента, блокирующего операции get для свойств, которые начинаются с символа подчеркивания.  
  
```JavaScript  
var p = new Proxy({}, {  
    get(k, t, r) {  
        // return undefined if key begins with underscore  
        if(k[0] === '_') return undefined;  
  
       // otherwise do default behavior  
       return Reflect.get(k, t, r);  
    }  
});  
  
p._foo = 1;  
console.log(p._foo);  
  
p.foo = 1;  
console.log(p.foo);  
  
// Output:  
// undefined  
// 1  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]