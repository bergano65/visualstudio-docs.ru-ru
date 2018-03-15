---
title: "Оператор typeof (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- typeof_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- typeof operator
ms.assetid: ee8a1036-119f-486f-b034-b07bdba87f0c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9ff8c7942c773d138dd599956c41d1e583e6288
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2018
---
# <a name="typeof-operator-javascript"></a>Оператор typeof (JavaScript)
Возвращает строку, которая идентифицирует тип данных выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
typeof[(]expression[)] ;  
```  
  
## <a name="remarks"></a>Примечания  
 *Выражение* аргумент — выражение, для которого выполняется поиск информации.  
  
 `typeof` Оператор возвращает сведения о типе в виде строки. Существует семь возможные значения, `typeof` возвращает: «число», «строку» «boolean», «объекта» «функции» «undefined» и «неизвестно».  
  
 В скобках необязательны `typeof` синтаксиса.  

 Объект может возвратить в XMLHTTPRequest неизвестного типа. COM-объекта с не аналогом в JavaScript могут также возвращать в неизвестный тип.
  
## <a name="example"></a>Пример  
 В следующем примере проверяется тип данных переменных.  
  
```JavaScript  
var index = 5;  
var result = (typeof index === 'number');  
// Output: true  
  
var description = "abc";  
var result = (typeof description === 'string');  
// Output: true  
```  
  
## <a name="example"></a>Пример  
 В следующем примере проверяется для типа данных `undefined` для переменных, объявленных и необъявленных.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Функция Array.isArray](../../javascript/reference/array-isarray-function-javascript.md)   
 [Функция Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [Константа undefined](../../javascript/reference/undefined-constant-javascript.md)   
 [Операторы сравнения](../../javascript/reference/comparison-operators-javascript.md)   
 [Типы данных](../../javascript/data-types-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)