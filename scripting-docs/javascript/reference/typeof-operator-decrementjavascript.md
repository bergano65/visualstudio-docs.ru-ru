---
title: "Оператор typeof (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: typeof_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: typeof operator
ms.assetid: ee8a1036-119f-486f-b034-b07bdba87f0c
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c79c69e6c447b14e61fa67ccb8600d5d83bebd2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="typeof-operator-javascript"></a>Оператор typeof (JavaScript)
Возвращает строку, которая идентифицирует тип данных выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
typeof[(]expression[)] ;  
```  
  
## <a name="remarks"></a>Примечания  
 *Выражение* аргумент — выражение, для которого выполняется поиск информации.  
  
 `typeof` Оператор возвращает сведения о типе в виде строки. Существует шесть возможные значения, `typeof` возвращает: «число», «строку» «boolean», «,» «функция» и «undefined».  
  
 В скобках необязательны `typeof` синтаксиса.  
  
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