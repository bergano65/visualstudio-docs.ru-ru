---
title: "Функция Math.min (JavaScript) | Документы Microsoft"
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
- min
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- min method
ms.assetid: a1d7dd85-27ef-45cd-aa2a-f8e80f0b2898
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb496cff65db11cf6c99d6a6e687f39e20ea857c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="mathmin-function-javascript"></a>Функция Math.min (JavaScript)
Возвращает наименьшее значение из набора числовых выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Math.min([number1[, number2[... [,numberN]]]])  
```  
  
## <a name="remarks"></a>Примечания  
 Необязательный `number1, number2, ..., numberN` аргументы являются числовые выражения для оценки.  
  
 Если аргументы не предоставлены, возвращаемое значение равно [Number.POSITIVE_INFINITY](../../javascript/reference/number-constants-javascript.md). Если любой из аргументов `NaN`, возвращаемое значение также является `NaN`.  
  
## <a name="example"></a>Пример  
 Следующий код показывает способ получения меньшее из двух выражений.  
  
```JavaScript  
var x = Math.min(107 - 3, 48 * 90);  
document.write(x);  
  
// Output:  
// 104  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Функция Math.max](../../javascript/reference/math-max-function-javascript.md)