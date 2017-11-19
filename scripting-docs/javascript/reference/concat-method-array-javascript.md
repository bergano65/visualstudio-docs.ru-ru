---
title: "Метод concat (массив) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: concat
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- concat method (array)
- Concat method
ms.assetid: bc2b4a6a-209e-4d59-8c24-59db01d53b1e
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 19f3a216a36f9ad8c422036476e46b89b6ee488c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="concat-method-array-javascript"></a>Метод concat (массив) (JavaScript)
Объединяет два или более массива.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
array1.concat([item1[, item2[, . . . [, itemN]]]])   
```  
  
## <a name="parameters"></a>Параметры  
 `array1`  
 Обязательный. `Array` Объекта, для которого объединяются другие массивы.  
  
 `item1,. . ., itemN`  
 Необязательно. Дополнительные элементы для добавления в конец `array1`.  
  
## <a name="remarks"></a>Примечания  
 `concat` Возвращает `Array` объект, содержащий результат объединения `array1` и любыми другими предоставленными элементами.  
  
 Добавление элементов (*item1 itemN*) в массиве будут добавлены, по порядку, начиная с первого элемента в списке. Если один из элементов является массивом, его содержимое добавляется в конец `array1`. Если не является массивом, он добавляется в конец массива как один элемент массива.  
  
 Элементы исходные массивы копируются в результирующий массив следующим образом:  
  
-   Если объект копируется из одного из массивов, объединяемых в новый массив, ссылка на объект продолжает указывать на тот же объект. Изменение в новом массиве или исходный массив приведет изменение в другой.  
  
-   Если значение, число или строка добавляется в новый массив, копируется только значение. Изменение значения в одном массиве не влияет на значение в другом.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать `concat` метод при использовании массива:  
  
```JavaScript  
var a, b, c, d;  
a = new Array(1,2,3);  
b = "dog";  
c = new Array(42, "cat");  
d = a.concat(b, c);  
document.write(d);  
  
//Output:   
1, 2, 3, "dog", 42, "cat"  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Метод concat (строка)](../../javascript/reference/concat-method-string-javascript.md)   
 [Метод join (Array)](../../javascript/reference/join-method-array-javascript.md)