---
title: "Свойство prototype (Object) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Prototype
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- inheritance, objects
- Prototype property
ms.assetid: 9fc434a1-5995-4fcb-a4e8-00e7f615aaa2
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a73d213b6b17f5046eb1f4c498aeb223f942f2d8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-object-javascript"></a>Свойство prototype (Object) (JavaScript)
Возвращает ссылку на прототип класса объектов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
objectName.prototype  
```  
  
## <a name="remarks"></a>Примечания  
 Аргумент `objectName` является именем объекта.  
  
 Чтобы для класса объектов обеспечить базовый набор функциональности, используйте свойство `prototype`. Новые экземпляры объекта "наследуют" поведение прототипа, назначенного этому объекту.  
  
 Например, чтобы добавить метод в объект `Array`, возвращающий значение самого большого элемента массива, объявите функцию, добавьте ее в `Array.prototype`, а затем используйте его.  
  
```JavaScript  
function array_max( ){  
    var i, max = this[0];  
    for (i = 1; i < this.length; i++)  
    {  
    if (max < this[i])  
    max = this[i];  
    }  
    return max;  
}  
Array.prototype.max = array_max;  
var myArray = new Array(7, 1, 3, 11, 25, 9  
);  
document.write(myArray.max());  
  
// Output:  
// 25  
  
```  
  
 Все встроенные [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] объекты имеют `prototype` свойство, которое доступно только для чтения. Свойства и методы могут быть добавлены в прототип, но объект нельзя назначить другому прототипу. Тем не менее определенных пользователем объектов можно назначить новый прототип.  
  
 Списках методов и свойств для каждого встроенного объекта в этом справочнике по языку указывают, какие из них являются частью прототип объекта, а какие — нет.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Свойство constructor (Object)](../../javascript/reference/constructor-property-object-javascript.md)