---
title: "Оператор typeof (JavaScript) | Microsoft Docs"
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
  - "typeof_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "typeof - оператор"
ms.assetid: ee8a1036-119f-486f-b034-b07bdba87f0c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Оператор typeof (JavaScript)
Возвращает строку, которая идентифицирует тип данных в выражении.  
  
## Синтаксис  
  
```  
  
typeof[(]expression[)] ;  
```  
  
## Заметки  
 Аргумент *expression* — это любое выражение, для которого требуется получить информацию о типе.  
  
 Оператор `typeof` возвращает данные о типе в виде строки.  Предусмотрено шесть возможных значений, возвращаемых оператором `typeof`: "number", "string", "boolean", "object", "function" и "undefined".  
  
 Скобки в синтаксисе оператора `typeof` необязательны.  
  
## Пример  
 В следующем примере проверяется тип данных переменных.  
  
```javascript  
var index = 5;  
var result = (typeof index === 'number');  
// Output: true  
  
var description = "abc";  
var result = (typeof description === 'string');  
// Output: true  
```  
  
## Пример  
 В следующем примере проверяется тип данных `undefined` для объявленных и необъявленных переменных.  
  
```javascript  
var declared;  
var result = (declared === undefined);  
// Output: true  
  
var result = (typeof declared === 'undefined');  
// Output: true  
  
var result = (typeof notDeclared === 'undefined')  
// Output: true  
  
var obj = {};  
var result = (typeof obj.propNotDeclared === 'undefined');  
// Output: true  
  
// An undeclared variable cannot be used in a comparison without  
// the typeof operator, so the next line generates an error.  
//  var result = (notDeclared === undefined);  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Функция Array.isArray](../../javascript/reference/array-isarray-function-javascript.md)   
 [Функция Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [Константа undefined](../../javascript/reference/undefined-constant-javascript.md)   
 [Операторы сравнения](../../javascript/reference/comparison-operators-javascript.md)   
 [Типы данных](../../javascript/data-types-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)