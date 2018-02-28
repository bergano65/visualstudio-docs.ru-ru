---
title: "Метод splice (Array) (JavaScript) | Документы Microsoft"
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
- splice
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- splice method
ms.assetid: 85fdfb13-e3d9-4c89-b524-3ccee7001c93
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d56a22244f76f5ce7221c276629907811733d51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="splice-method-array-javascript"></a>Метод splice (Array) (JavaScript)
Удаляет элементы из массива и при необходимости вставляет на их место новые элементы, возвращая удаленные элементы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
arrayObj.splice(start, deleteCount, [item1[, item2[, . . . [,itemN]]]])  
```  
  
## <a name="parameters"></a>Параметры  
 `arrayObj`  
 Обязательный. Объект `Array`.  
  
 `start`  
 Обязательный. Отсчитываемый от нуля расположение в массиве, с которой начинается удаление элементов.  
  
 `deleteCount`  
 Обязательный. Число удаляемых элементов.  
  
 `item1, item2,. . ., itemN`  
 Необязательно. Элементы, вставить в массив вместо удаленных элементов.  
  
## <a name="remarks"></a>Примечания  
 `splice` Изменяет метод `arrayObj` , удалив указанное число элементов от позиции `start` и вставка новых элементов. Удаленные элементы возвращаются в виде нового `Array` объекта.  
  
## <a name="example"></a>Пример  
 В следующем примере кода демонстрируется применение метода `splice`.  
  
```JavaScript  
var arr = new Array("4", "11", "2", "10", "3", "1");  
arr.splice(2, 2, "21", "31");  
document.write(arr);  
  
// Output: 4,11,21,31,3,1  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Метод slice (массив)](../../javascript/reference/slice-method-array-javascript.md)