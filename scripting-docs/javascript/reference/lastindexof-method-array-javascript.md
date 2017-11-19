---
title: "Метод lastIndexOf (массив) (JavaScript) | Документы Microsoft"
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
helpviewer_keywords:
- arrays [JavaScript], lastIndexOf method
- lastIndexOf method [JavaScript]
ms.assetid: 04f5145d-007e-498f-b06f-11ab384c2968
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12d2a0fca7a7cd82543a83ea19aca49d3cbb93b6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="lastindexof-method-array-javascript"></a>Метод lastIndexOf (массив) (JavaScript)
Возвращает индекс последнего вхождения указанного значения в массиве.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
array1.lastIndexOf(searchElement[, fromIndex])  
```  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Определение|  
|---------------|----------------|  
|`array1`|Обязательный. Объект массива для поиска.|  
|`searchElement`|Обязательный. Значение для поиска в `array1`.|  
|`fromIndex`|Необязательно. Индекс в массиве, с которого начинается поиск. Если `fromIndex` — этот параметр опущен, поиск начинается с последнего индекса в массиве.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Индекс последнего вхождения `searchElement` в массиве или -1, если `searchElement` не найден.  
  
## <a name="remarks"></a>Примечания  
 `lastIndexOf` Метод ищет массив для указанного значения. Метод возвращает индекс первого вхождения или -1, если указанное значение не найдено.  
  
 Поиск выполняется в порядке убывания индекса (Фамилия члена имя). Для поиска в порядке возрастания, используйте [метод indexOf (массив)](../../javascript/reference/indexof-method-array-javascript.md).  
  
 Элементы массива, сравниваются с `searchElement` значение на строгое равенство, аналогично сравнения, выполненные `===` оператор. Дополнительные сведения см. в разделе [операторы сравнения](../../javascript/reference/comparison-operators-javascript.md).  
  
 Необязательный `fromIndex` аргумент задает индекс массива, с которого начинается поиск. Если `fromIndex` больше или равен длине массива, весь массив выполняется поиск. Если `fromIndex` имеет отрицательное значение, поиск начинается плюс длина массива `fromIndex`. Если вычисляемый индекса меньше 0, возвращается значение -1.  
  
## <a name="example"></a>Пример  
 Следующие примеры иллюстрируют использование `lastIndexOf` метода.  
  
```JavaScript  
// Create an array.  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location, in descending order, of "cd".  
document.write(ar.lastIndexOf("cd") + "<br/>");  
  
// Output: 4  
  
// Find "cd" in descending order, starting at index 2.  
document.write(ar.lastIndexOf("cd", 2) + "<br/>");  
  
// Output: 1  
  
// Search for "gh" (which is not found).  
document.write(ar.lastIndexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -3.  
// The search in descending order starts at index 3,  
// which is the array length minus 2.  
document.write(ar.lastIndexOf("ab", -3) + "<br/>");  
// Output: 0  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Метод indexOf (массив)](../../javascript/reference/indexof-method-array-javascript.md)   
 [Объект Array](../../javascript/reference/array-object-javascript.md)   
 [Использование массивов](../../javascript/advanced/using-arrays-javascript.md)