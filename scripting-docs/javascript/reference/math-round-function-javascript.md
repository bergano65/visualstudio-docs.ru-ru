---
title: "Функция Math.Round (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: round
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Round method
- Math object
ms.assetid: 51008df3-5d0c-4951-84cb-4f41000db0be
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9543d529e3d0e4e45cff29f1286edbfad8dc0e27
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="mathround-function-javascript"></a>Функция Math.round (JavaScript)
Возвращает указанное числовое выражение, округленное до ближайшего целого.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Math.round(  
number  
)   
```  
  
## <a name="remarks"></a>Примечания  
 Необходимая `number` аргумент имеет значение должно быть округлено до ближайшего целого.  
  
 Для положительных чисел Если дробная часть `number` превышает 0,5, возвращаемое значение равно наименьшее целое число, большее `number`. Если дробная часть меньше 0,5, возвращаемое значение — наибольшее целое число меньше или равно `number`.  
  
 Для отрицательных чисел: Если дробная часть равна -0,5, возвращаемым значением является наименьшее целое число, большее число.  
  
 Например `Math.round(8.5)` возвращает 9, но `Math.round(-8.5)` возвращает -8.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применяется к**: [объект Math](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Функция Math.random](../../javascript/reference/math-random-function-javascript.md)