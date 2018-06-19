---
title: Свойство constructor (Object) (JavaScript) | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- constructor
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- constructor property
ms.assetid: 6f5d0e9d-e85f-4fde-b558-744510483d69
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 569dab69906aa167ef486923bd7ceb7455ac243e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636264"
---
# <a name="constructor-property-object-javascript"></a>Свойство constructor (Object) (JavaScript)
Указывает функцию, которая создает объект.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.constructor  
```  
  
## <a name="remarks"></a>Примечания  
 Необходимая `object` имя объекта или функции.  
  
 Свойство `constructor` является членом прототипа каждого объекта, который имеет прототип. Сюда входят все встроенные [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] объектов, за исключением `Global` и `Math` объектов. Свойство `constructor` содержит ссылку на функцию, которая создает экземпляры конкретного объекта.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование свойства конструктора.  
  
```JavaScript  
// A constructor function.  
function MyObj() {  
    this.number = 1;  
}  
  
var x = new String("Hi");  
  
if (x.constructor == String)  
    document.write("Object is a String.");  
document.write ("<br />");  
  
var y = new MyObj;  
if (y.constructor == MyObj)  
    document.write("Object constructor is MyObj.");  
  
// Output:  
// Object is a String.  
// Object constructor is MyObj.  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Свойство prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)