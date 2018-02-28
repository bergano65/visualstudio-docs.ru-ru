---
title: "Функция Math.max (JavaScript) | Документы Microsoft"
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
- max
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- max method
ms.assetid: f3ea1b8a-5fd0-482a-971b-b7f8e2b9b7eb
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: adf66164346f3802d92f8e0de82356df49bad5fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="mathmax-function-javascript"></a>Функция Math.max (JavaScript)
Возвращает большее из набора числовых выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Math.max([number1[, number2[... [, numberN]]]])   
```  
  
## <a name="remarks"></a>Примечания  
 Необязательный `number1, number2, ..., numberN` аргументы являются числовые выражения для оценки.  
  
 Если аргументы не предоставлены, возвращаемое значение равно [Number.NEGATIVE_INFINITY](../../javascript/reference/number-constants-javascript.md). Если любой из аргументов `NaN`, возвращаемое значение также является `NaN`.  
  
## <a name="example"></a>Пример  
 Следующий код показывает способ получения большее из двух выражений.  
  
```JavaScript  
var x = Math.max(107 - 3,  48 * 90);  
document.write(x);  
  
// Output:  
// 4320  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Функция Math.min](../../javascript/reference/math-min-function-javascript.md)