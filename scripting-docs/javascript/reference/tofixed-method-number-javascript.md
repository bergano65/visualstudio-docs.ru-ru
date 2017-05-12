---
title: "Метод toFixed (Number) (JavaScript) | Microsoft Docs"
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
  - "toFixed"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toFixed - метод"
ms.assetid: b5f03400-865e-4ab2-818c-f734c0f6d6f0
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Метод toFixed (Number) (JavaScript)
Представляет число в нотации с фиксированной запятой.  
  
## Синтаксис  
  
```  
  
numObj.toFixed([fractionDigits])  
```  
  
## Параметры  
 `numObj`  
 Требуемый параметр. Объект `Number`.  
  
 `fractionDigits`  
 Необязательный параметр.  Количество цифр после десятичной запятой.  Это число должно находиться в диапазоне от 0 до 20 включительно.  
  
## Возвращаемое значение  
 Возвращает строковое представление числа в нотации с фиксированной запятой, содержащего цифры `fractionDigits` после десятичной запятой.  
  
 Если `fractionDigits` не указан или **undefined**, то значение по умолчанию равно нулю.  
  
## Пример  
 Следующий код показывает, как использовать функцию `toFixed`.  
  
```javascript  
var num = new Number(123);  
var fix = num.toFixed();  
document.write(fix);  
document.write("<br/>");  
  
num = new Number(123.456);  
fix = num.toFixed(5);  
document.write(fix);  
  
// Output:  
// 123  
123.45600  
  
```  
  
## Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Применение**: [Объект Number](../../javascript/reference/number-object-javascript.md)  
  
## См. также  
 [Метод toExponential \(Number\)](../../javascript/reference/toexponential-method-number-javascript.md)   
 [Метод toPrecision \(Number\)](../../javascript/reference/toprecision-method-number-javascript.md)