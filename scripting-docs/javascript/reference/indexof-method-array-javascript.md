---
title: Метод indexOf (массив) (JavaScript) | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [JavaScript], indexOf method
- indexOf method [JavaScript]
ms.assetid: 5bee31ae-aaf1-4466-8cfd-ed287e3cdf17
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63685219faf42991da6b798493c58b356ab97279
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637484"
---
# <a name="indexof-method-array-javascript"></a>Метод indexOf (массив) (JavaScript)
Возвращает индекс первого вхождения значения в массиве.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
array1.indexOf(searchElement[, fromIndex])  
```  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Определение|  
|---------------|----------------|  
|`array1`|Обязательный. Объект массива.|  
|`searchElement`|Обязательный. Значение для поиска в `array1`.|  
|`fromIndex`|Необязательно. Индекс в массиве, с которого начинается поиск. Если `fromIndex` — этот параметр опущен, поиск начинается с индексом 0.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Индекс первого вхождения `searchElement` в массиве или -1, если `searchElement` не найден.  
  
## <a name="remarks"></a>Примечания  
 `indexOf` Метод ищет массив для указанного значения. Метод возвращает индекс первого вхождения или -1, если указанное значение не найдено.  
  
 Поиск выполняется в порядке возрастания индекса.  
  
 Элементы массива, сравниваются с `searchElement` значение на строгое равенство, аналогично `===` оператор. Дополнительные сведения см. в разделе [операторы сравнения](../../javascript/reference/comparison-operators-javascript.md).  
  
 Необязательный `fromIndex` аргумент задает индекс массива, с которого начинается поиск. Если `fromIndex` больше или равен длине массива, возвращается значение -1. Если `fromIndex` имеет отрицательное значение, поиск начинается плюс длина массива `fromIndex`.  
  
## <a name="example"></a>Пример  
 Следующие примеры иллюстрируют использование `indexOf` метода.  
  
```JavaScript  
// Create an array. (The elements start at index 0.)  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location of "cd".  
document.write(ar.indexOf("cd") + "<br/>");  
  
// Output: 1  
  
// Find "cd" starting at index 2.  
document.write(ar.indexOf("cd", 2) + "<br/>");  
  
// Output: 4  
  
// Find "gh" (which is not found).  
document.write (ar.indexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -2.  
// The search starts at index 3, which is the array length plus -2.  
document.write (ar.indexOf("ab", -2) + "<br/>");  
// Output: 3  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Методы JavaScript](../../javascript/reference/javascript-methods.md)   
 [Объект Array](../../javascript/reference/array-object-javascript.md)   
 [Использование массивов](../../javascript/advanced/using-arrays-javascript.md)