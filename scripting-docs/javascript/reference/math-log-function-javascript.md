---
title: "Функция Math.log (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "log"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "log - метод"
  - "Math - объект"
ms.assetid: 5d617fb5-4b27-404e-842f-eea5549a7c1a
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Функция Math.log (JavaScript)
Возвращает натуральный логарифм \(с основанием `e`\) от числа.  
  
## Синтаксис  
  
```  
Math.log(number)   
```  
  
#### Параметры  
 number  
 Число.  
  
## Возвращаемое значение  
 Если значение `number` положительно, эта функция возвращает натуральный логарифм числа.  Если значение `number` отрицательно, эта функция возвращает значение `NaN`.  Если значение `number` равно 0, то эта функция возвращает `-Infinity`.  
  
## Пример  
 Следующий код показывает, как использовать эту функцию.  
  
```javascript  
var numArr = [ 45.3, 69.0, 557.04, 0.222 ];  
  
for (i in numArr) {  
    document.write(Math.log(numArr[i]));  
    document.write("<br/>");  
}  
  
// Output:   
// 3.8133070324889884  
// 4.23410650459726  
// 6.322637050634291  
// -1.5050778971098575  
  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применение**: [Объект Math](../../javascript/reference/math-object-javascript.md)  
  
## См. также  
 [Функция Math.sqrt](../../javascript/reference/math-sqrt-function-javascript.md)