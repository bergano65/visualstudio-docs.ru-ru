---
title: "Метод toPrecision (Number) (JavaScript) | Microsoft Docs"
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
  - "toPrecision"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toPrecision - метод"
ms.assetid: ac13c82f-1038-447a-823f-f755bba535ca
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Метод toPrecision (Number) (JavaScript)
Представляет число в экспоненциальной нотации или в нотации с фиксированной запятой с указанным количеством знаков.  
  
## Синтаксис  
  
```  
  
numObj.toPrecision([precision])  
```  
  
## Параметры  
 `numObj`  
 Обязательный.  Объект `Number`.  
  
 `precision`  
 Необязательный.  Количество значащих цифр.  Это число должно находиться в диапазоне от 1 до 21 включительно.  
  
## Возвращаемое значение  
 Для чисел в экспоненциальной нотации возвращается число знаков после запятой, равное `precision` \- 1.  Для чисел в нотации с фиксированной запятой возвращается число значащих цифр, равное значению `precision`.  
  
 Если значение `precision` не указано или равно **undefined**, вызывается метод **toString**.  
  
## Пример  
 Следующий код показывает, как использовать метод `toPrecision`.  
  
```javascript  
var num = new Number(123);  
var prec = num.toPrecision();  
document.write(prec);  
document.write("<br/>");  
  
num = new Number(123.456);  
prec = num.toPrecision(5);  
document.write(prec);  
  
// Output:  
// 123  
// 123.46  
  
```  
  
## Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Относится к**: [Объект Number](../../javascript/reference/number-object-javascript.md)  
  
## См. также  
 [Метод toFixed \(Number\)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [Метод toExponential \(Number\)](../../javascript/reference/toexponential-method-number-javascript.md)