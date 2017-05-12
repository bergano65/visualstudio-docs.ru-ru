---
title: "Функция Math.abs (JavaScript) | Microsoft Docs"
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
  - "abs"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "абсолютные значения, вычисление"
  - "абсолютные значения"
  - "числовые выражения"
  - "abs - метод"
ms.assetid: 9af4b5b8-de77-47bb-bb59-abdde371e4c3
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Функция Math.abs (JavaScript)
Возвращает абсолютное значение числа \(значение вне зависимости от того, положительное оно или отрицательное\).  Например, абсолютное значение числа \-5 такое же, как абсолютное значение числа 5.  
  
## Синтаксис  
  
```  
Math.abs(number)  
```  
  
#### Параметры  
 Обязательный аргумент `number` — это числовое выражение, для которого требуется абсолютное значение.  
  
## Возвращаемое значение  
 Абсолютное значение аргумента `number`.  
  
## Пример  
 В следующем примере показано, как используется функция `abs`.  
  
```javascript  
var s;  
var v1 = Math.abs(6);  
var v2 = Math.abs(-6);  
if (v1 == v2) {  
    document.write("Absolute values are the same.");  
}  
else {  
document.write("Absolute values are different.");  
}  
  
// Output: Absolute values are the same.  
  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применение**: [Объект Math](../../javascript/reference/math-object-javascript.md)  
  
## См. также  
 [Объект Math](../../javascript/reference/math-object-javascript.md)