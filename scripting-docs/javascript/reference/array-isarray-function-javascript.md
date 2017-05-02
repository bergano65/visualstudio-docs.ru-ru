---
title: "Функция Array.isArray (JavaScript) | Microsoft Docs"
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
  - "Array.isArray - функция [JavaScript]"
  - "isArray - функция [JavaScript]"
ms.assetid: 58f7d2e0-d310-4292-b9bc-37a73c585780
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Функция Array.isArray (JavaScript)
Определяет, является ли объект массивом.  
  
## Синтаксис  
  
```  
Array.isArray(object)   
```  
  
#### Параметры  
 `object`  
 Обязательный.  Объект для тестирования.  
  
## Возвращаемое значение  
 Значение `true`, если `object` является массивом; в противном случае — значение `false`.  Если аргумент `object` не является объектом, возвращается `false`.  
  
## Пример  
 В следующем примере показано применение функции `Array.isArray`.  
  
```javascript  
var ar = [];  
var result = Array.isArray(ar);  
// Output: true  
  
var ar = new Array();  
var result = Array.isArray(ar);  
// Output: true  
  
var ar = [1, 2, 3];  
var result = Array.isArray(ar);  
// Output: true  
  
var result = Array.isArray("an array");  
document.write(result);  
// Output: false  
```  
  
## Требования  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## См. также  
 [Объект Array](../../javascript/reference/array-object-javascript.md)   
 [Использование массивов](../../javascript/advanced/using-arrays-javascript.md)   
 [Оператор typeof](../../javascript/reference/typeof-operator-decrementjavascript.md)