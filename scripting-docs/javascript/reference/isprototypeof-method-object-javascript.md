---
title: "Метод isPrototypeOf (Object) (JavaScript) | Документы Microsoft"
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
- isPrototypeOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- isPrototypeOf method
ms.assetid: 9c821319-c208-480f-915e-565ef6e017b6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47ce97faecfade089bbf0b7a725a02ee73b54718
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="isprototypeof-method-object-javascript"></a>Метод isPrototypeOf (Object) (JavaScript)
Определяет, существует ли объект в цепочке прототипов другого объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
prototype.isPrototypeOf(object)  
```  
  
## <a name="parameters"></a>Параметры  
 `prototype`  
 Обязательный. Прототип объекта.  
  
 `object`  
 Обязательный. Другой объект, цепочку прототипов которого требуется проверить.  
  
## <a name="remarks"></a>Примечания  
 Метод `isPrototypeOf` возвращает значение `true`, если `object` содержит `prototype` в своей цепочке прототипов. Цепочка прототипов служит для совместного использования функциональных возможностей несколькими экземплярами одного типа объектов. Метод `isPrototypeOf` возвращает значение `false`, если `object` не является объектом или если `prototype` отсутствует в цепочке прототипов объекта `object`.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода `isPrototypeOf`.  
  
```JavaScript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
document.write(Rectangle.prototype.isPrototypeOf(rec));  
  
// Output: true  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Свойство prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)