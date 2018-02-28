---
title: "Метод unshift (Array) (JavaScript) | Документы Microsoft"
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
- unshift
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- unshift method
ms.assetid: 8c6a39ed-bab3-4ca4-9350-571a9427ec94
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c3f0d210514d04afa5cf467819a5e843925e1a68
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="unshift-method-array-javascript"></a>Метод unshift (Array) (JavaScript)
Вставляет новые элементы в начало массива.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
arrayObj.unshift([item1[, item2 [, . . . [, itemN]]]])  
```  
  
## <a name="parameters"></a>Параметры  
 `arrayObj`  
 Обязательный. Объект `Array`.  
  
 `item1, item2,. . ., itemN`  
 Необязательно. Элементы для вставки в начале `Array`.  
  
## <a name="remarks"></a>Примечания  
 `unshift` Метод вставляет элементы в начало массива, поэтому они появляются в том же порядке, в котором они отображаются в списке аргументов.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода `unshift`.  
  
```JavaScript  
var ar = new Array();  
ar.unshift(10, 11);  
ar.unshift(12, 13, 14);  
document.write(ar.toString());  
  
// Output: 12,13,14,10,11  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Метод shift (Array)](../../javascript/reference/shift-method-array-javascript.md)