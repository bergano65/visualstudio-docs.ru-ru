---
title: "Метод toExponential (Number) (JavaScript) | Microsoft Docs"
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
  - "toExponential"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toExponential - метод"
ms.assetid: 7c4a6d84-3c1f-4cc4-a67d-7753e5d4ed66
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Метод toExponential (Number) (JavaScript)
Представляет число в экспоненциальной нотации.  
  
## Синтаксис  
  
```  
  
numObj. toExponential([fractionDigits])  
```  
  
## Параметры  
 `numObj`  
 Обязательный.  Объект **Number**.  
  
 `fractionDigits`  
 Необязательный.  Количество разрядов после десятичной запятой.  Это число должно находиться в диапазоне от 0 до 20 включительно.  
  
## Возвращаемое значение  
 Возвращает строковое представление числа в экспоненциальной нотации.  Строка содержит одну цифру перед десятичной запятой, а после запятой может содержать то количество цифр, которое указано в параметре `fractionDigits`.  
  
 Если параметр `fractionDigits` не указан, метод `toExponential` возвращает столько цифр, сколько необходимо для уникального определения числа.  
  
## Пример  
  
```javascript  
var num = new Number(123);  
var exp = num.toExponential();  
document.write(exp);  
document.write("<br/>");  
  
num = new Number(123.456);  
exp = num.toExponential(5);  
document.write(exp);  
  
// Output:   
// 1.23e+2  
// 1.23456e+2  
  
```  
  
## Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Относится к**: [Объект Number](../../javascript/reference/number-object-javascript.md)  
  
## См. также  
 [Метод toFixed \(Number\)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [Метод toPrecision \(Number\)](../../javascript/reference/toprecision-method-number-javascript.md)