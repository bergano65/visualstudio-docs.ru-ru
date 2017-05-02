---
title: "Математические константы (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "LN2 - константа [JavaScript]"
  - "E - константа [JavaScript]"
  - "LOG10E - константа [JavaScript]"
  - "SQRT1_2 - константа [JavaScript]"
  - "LOG2E - константа [JavaScript]"
  - "Math.SQRT2 - константа [JavaScript]"
  - "PI - константа [JavaScript]"
  - "Math.LOG2E - константа [JavaScript]"
  - "константы [JavaScript], математические"
  - "Math.E - константа [JavaScript]"
  - "логарифмические константы [JavaScript]"
  - "Math.LOG10E - константа [JavaScript]"
  - "Math.SQRT1_2 - константа [JavaScript]"
  - "SQRT2 - константа [JavaScript]"
  - "константы квадратного корня [JavaScript]"
  - "Math.PI - константа [JavaScript]"
  - "математические константы [JavaScript]"
  - "LN10 - константа [JavaScript]"
  - "Math.LN2 - константа [JavaScript]"
  - "Math.LN10 - константа [JavaScript]"
ms.assetid: 8a674046-cb99-4103-92be-83697fba6344
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Математические константы (JavaScript)
Математические константы возвращают постоянные значения, которые являются свойствами объекта `Math`.  
  
## Константы объекта Math  
 В следующей таблице перечислены константные значения, которые являются свойствами [Объекта Math](../../javascript/reference/math-object-javascript.md).  
  
|Константа|Описание|Приблизительное значение|  
|---------------|--------------|------------------------------|  
|`Math.E`|Математическая константа e.  Это число Эйлера — основание натурального логарифма.|2.718|  
|`Math.LN2`|Натуральный логарифм от числа 2.|0.693|  
|`Math.LN10`|Натуральный логарифм от числа 10.|2.302|  
|`Math.LOG2E`|Логарифм по основанию 2 от числа e.|1.443|  
|`Math.LOG10E`|Логарифм по основанию 10 от числа e.|0.434|  
|`Math.PI`|Число Пи.  Это соотношение длины окружности к ее диаметру.|3.14159|  
|`Math.SQRT1_2`|Квадратный корень числа 0,5 что эквивалентно результату деления единицы на квадратный корень числа 2.|0.707|  
|`Math.SQRT2`|Квадратный корень из числа 2.|1.414|  
  
## Пример  
 В следующем примере показано, как использовать константу `Math.PI`.  
  
```javascript  
var radius = 3;  
var area = Math.PI * radius * radius;  
document.write(area);  
  
// Output: 28.274333882308138  
  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применение**: [Объект Math](../../javascript/reference/math-object-javascript.md)  
  
## См. также  
 [Числовые константы](../../javascript/reference/number-constants-javascript.md)   
 [Константы JavaScript](../../javascript/reference/javascript-constants.md)