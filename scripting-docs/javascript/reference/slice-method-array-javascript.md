---
title: "Метод slice (Array) (JavaScript) | Документы Microsoft"
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
- slice
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- zero-based index
- Array object
- slice method
ms.assetid: 3c122219-14de-4126-b091-809659c026d6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a61cd331abef9d1a0d979f547f6d6f12222c1eee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="slice-method-array-javascript"></a>Метод slice (Array) (JavaScript)
Возвращает фрагмент массива.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
arrayObj.slice(start, [end])   
```  
  
## <a name="parameters"></a>Параметры  
 `arrayObj`  
 Обязательный. Объект `Array`.  
  
 `start`  
 Обязательный. Начало заданную часть `arrayObj`.  
  
 `end`  
 Необязательно. Конец заданную часть `arrayObj`.  
  
## <a name="remarks"></a>Примечания  
 `slice` Возвращает `Array` объект, содержащий указанную часть `arrayObj`.  
  
 `slice` Метод копирует до, но не включая элемент, указанный по `end`. Если `start` имеет отрицательное значение, он рассматривается как `length`  +  `start`, где `length` длина массива. Если `end` имеет отрицательное значение, он рассматривается как `length`  +  `end` где `length` длина массива. Если параметр `end` не задан, извлечение продолжается до конца объекта `arrayObj`. Если `end` предшествует `start`, элементы копируются в новый массив.  
  
## <a name="example"></a>Пример  
 В следующем примере демонстрируется использование метода `slice`. В первом примере, все, кроме последнего элемента `myArray` копируется в `newArray`. Во втором примере только последние два элемента `myArray` копируются в `newArray`.  
  
```JavaScript  
var origArray = [3, 5, 7, 9];  
var newArray = origArray. slice(0, -1);  
document.write(origArray);  
document.write("<br/>");  
newArray = origArray. slice(-2);  
document.write(newArray);  
  
// Output:  
// 3,5,7,9  
// 7,9  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Метод slice (строка)](../../javascript/reference/slice-method-string-javascript.md)   
 [Объект String](../../javascript/reference/string-object-javascript.md)