---
title: "Функция isNaN (JavaScript) | Документы Microsoft"
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
- isNaN
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- isNaN method
ms.assetid: 5af4eb29-72f6-484f-93bd-04ae1261f849
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b7e6d3687e795ea5d5e38308a8af0d73ba7f5ff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="isnan-function-javascript"></a>Функция isNaN (JavaScript)
Возвращает логическое значение, указывающее, является ли значение зарезервированным значением `NaN` (не числом).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
isNaN(numValue)   
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если значение преобразуется в тип `Number`, `true` имеет значение `NaN`; в противном случае — `false`.  
  
## <a name="remarks"></a>Примечания  
 Необходимая `numValue` это значение, которое нужно проверить вместе с `NaN`.  
  
 Обычно этот метод используется для проверки значений, возвращаемых методами `parseInt` и `parseFloat`.  
  
 Кроме того, переменная, содержащая `NaN` или другим значением может быть по сравнению с самого. Если сравнение указывает на неравенство, это `NaN`. Это вызвано `NaN` является единственным значением, которое не равно самому себе.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применяется к**: [глобального объекта](../../javascript/reference/global-object-javascript.md)  
  
## <a name="example"></a>Пример  
  
```JavaScript  
// Returns false.  
isNaN(100);  
  
// Returns false.  
isNaN("100");  
  
// Returns true.  
isNaN("ABC");  
  
// Returns true.  
isNaN("10C");  
  
// Returns true.  
isNaN("abc123");  
  
// Returns true.  
isNaN(Math.sqrt(-1));           
```  
  
## <a name="see-also"></a>См. также  
 [Функция isFinite](../../javascript/reference/isfinite-function-javascript.md)   
 [Константа NaN](../../javascript/reference/nan-constant-javascript.md)   
 [Функция parseFloat](../../javascript/reference/parsefloat-function-javascript.md)   
 [Функция parseInt](../../javascript/reference/parseint-function-javascript.md)