---
title: "Математические константы (JavaScript) | Документы Microsoft"
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
- LN2 constant [JavaScript]
- E constant [JavaScript]
- LOG10E constant [JavaScript]
- SQRT1_2 constant [JavaScript]
- LOG2E constant [JavaScript]
- Math.SQRT2 constant [JavaScript]
- PI constant [JavaScript]
- Math.LOG2E constant [JavaScript]
- constants [JavaScript], math
- Math.E constant [JavaScript]
- logarithm consants [JavaScript]
- Math.LOG10E constant [JavaScript]
- Math.SQRT1_2 constant [JavaScript]
- SQRT2 constant [JavaScript]
- square root constants [JavaScript]
- Math.PI constant [JavaScript]
- math constants [JavaScript]
- LN10 constant [JavaScript]
- Math.LN2 constant [JavaScript]
- Math.LN10 constant [JavaScript]
ms.assetid: 8a674046-cb99-4103-92be-83697fba6344
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9942abb69af416cd4cd7f092dc9f1478e0bc3a69
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="math-constants-javascript"></a>Математические константы (JavaScript)
Математические константы возвращают постоянные значения, которые являются свойствами `Math` объекта.  
  
## <a name="math-object-constants"></a>Константы объекта Math  
 В следующей таблице перечислены значения констант, которые являются свойствами [объекта Math](../../javascript/reference/math-object-javascript.md).  
  
|Константа|Описание|Приблизительное значение|  
|--------------|-----------------|-----------------------|  
|`Math.E`|Математическая константа e. Это число Эйлера, основа натуральных логарифмов.|2.718|  
|`Math.LN2`|Натуральный логарифм числа 2.|0.693|  
|`Math.LN10`|Натуральный логарифм числа 10.|2.302|  
|`Math.LOG2E`|Логарифм числа e по основанию 2.|1.443|  
|`Math.LOG10E`|Логарифм числа e по основанию 10.|0.434|  
|`Math.PI`|Число Пи. Отношение длины окружности к ее диаметру.|3.14159|  
|`Math.SQRT1_2`|Квадратный корень из 0,5 или единица, деленная на квадратный корень числа 2.|0.707|  
|`Math.SQRT2`|Квадратный корень из 2.|1.414|  
  
## <a name="example"></a>Пример  
 Следующий пример показывает, как использовать `Math.PI` константой.  
  
```JavaScript  
var radius = 3;  
var area = Math.PI * radius * radius;  
document.write(area);  
  
// Output: 28.274333882308138  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применяется к**: [объект Math](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Числовые константы](../../javascript/reference/number-constants-javascript.md)   
 [Константы JavaScript](../../javascript/reference/javascript-constants.md)