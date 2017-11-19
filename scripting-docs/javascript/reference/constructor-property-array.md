---
title: "Свойство constructor (Array) | Документы Microsoft"
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
ms.assetid: b78d517b-cb56-4866-b30f-ef8121a27843
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca779a2fa2356c1f3e1ca816f16531c0930459a4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-array"></a>Свойство constructor (Array)
Указывает функцию, которая создает массив.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
array.constructor  
```  
  
## <a name="remarks"></a>Примечания  
 Необходимая `array` имя массива.  
  
 Свойство `constructor` является членом прототипа каждого объекта, который имеет прототип. Сюда входят все встроенные [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] объектов, за исключением `Global` и `Math` объектов. Свойство `constructor` содержит ссылку на функцию, которая создает экземпляры конкретного объекта.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование свойства конструктора.  
  
```JavaScript  
var x = new Array();  
  
if (x.constructor == Array)  
    document.write("Object is an Array.");  
else  
    document.write("Object is not an Array.");  
  
// Output:  
// Object is an Array.  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]