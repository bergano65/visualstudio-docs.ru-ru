---
title: "Метод propertyIsEnumerable (Object) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- propertyIsEnumerable
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- propertyIsEnumerable property
ms.assetid: d90c7c2e-ea23-4710-a957-9aefbbd1f68b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5664732db6a311586f11eb13eee4407fdf81410f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="propertyisenumerable-method-object-javascript"></a>Метод propertyIsEnumerable (Object) (JavaScript)
Определяет, является ли указанное свойство enumerable.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object. propertyIsEnumerable(proName)  
```  
  
## <a name="parameters"></a>Параметры  
 `object`  
 Обязательный. Экземпляр объекта.  
  
 `proName`  
 Обязательный. Строковое значение имени свойства.  
  
## <a name="remarks"></a>Примечания  
 `propertyIsEnumerable` Возвращает `true` Если `proName` существует в `object` и могут быть перечислены с помощью `For` цикла. `propertyIsEnumerable` Возвращает `false` Если `object` отсутствует свойство с указанным именем или если указанное свойство не является перечислимым. Как правило предопределенные свойства не перечисляемую, но определяемые пользователем свойства всегда являются перечисляемыми.  
  
 `propertyIsEnumerable` Метод не учитывает объекты в цепочке прототипов.  
  
## <a name="example"></a>Пример  
  
```JavaScript  
var a = new Array("apple", "banana", "cactus");  
document.write(a.propertyIsEnumerable(1));  
  
// Output: true  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Свойство prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)