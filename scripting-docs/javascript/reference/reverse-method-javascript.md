---
title: "Метод reverse (JavaScript) | Документы Microsoft"
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
- reverse
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [Visual Studio], reversing elements
- reverse method
- transposing elements
ms.assetid: 02ab051b-79b8-4646-b502-381671e78c12
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a34385ccf89557688698b50384b3dfe359478df
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="reverse-method-javascript"></a>Метод reverse (JavaScript)
Изменяет элементы в `Array`.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
arrayObj.reverse()   
```  
  
## <a name="parameters"></a>Параметры  
 `arrayObj`  
 Обязательный. Любой объект `Array`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Обращенный массив.  
  
## <a name="remarks"></a>Примечания  
 Необходимая `arrayObj` ссылка `Array` объекта.  
  
 `reverse` Метод отменяет элементы `Array` объект на месте. Создает новый `Array` объекта во время выполнения.  
  
 Если массив не является непрерывным, `reverse` метод создает элементов в массиве, который заполнения пропусков в массиве. Каждый из этих вновь созданных элементов имеет значение `undefined`.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода `reverse`.  
  
```JavaScript  
var arr = new Array(0,1,2,3,4);   
var reverseArr = arr.reverse();  
document.write(reverseArr);  
  
// Output:  
// 4,3,2,1,0  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Метод concat (массив)](../../javascript/reference/concat-method-array-javascript.md)