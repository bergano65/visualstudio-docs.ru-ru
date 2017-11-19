---
title: "Операторы сравнения (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Comparison
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- comparison operators, script
- greater than operator
- comparison operators
- greater than or equal to operator
- inequity operator
- identity operator
ms.assetid: 084f90f0-d010-47cf-96dd-13d637fc9b68
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 067d570523fc2241b4f2e0442785a49aedb15200
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="comparison-operators-javascript"></a>Операторы сравнения (JavaScript)
Возвращает логическое значение, показывающее результат сравнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
expression1 comparisonoperator expression2  
```  
  
## <a name="parameters"></a>Параметры  
 `expression1`  
 Любое выражение.  
  
 `comparisonoperator`  
 Любой оператор сравнения.  
  
 `expression2`  
 Любое выражение.  
  
## <a name="remarks"></a>Примечания  
 При сравнении строк, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] использует значение символа Юникода строкового выражения.  
  
 Следующие описано поведение различных групп операторов в зависимости от того, типы и значения `expression1` и `expression2`:  
  
 Реляционные операторы: `<`, `>`, `<=`,`>=`  
  
-   Попытка преобразовать оба `expression1` и `expression2` в числа.  
  
-   Если оба выражения являются строками, сделайте сравнения строк.  
  
-   Если одно из выражений имеет `NaN`, возвращают `false`.  
  
-   Отрицательный нуль равен положительному нулю.  
  
-   Минус бесконечности меньше любых значений, включая сам.  
  
-   Плюс бесконечность больше любых значений, включая сам.  
  
 Операторы равенства: `==`,`!=`  
  
-   Если типы двух выражений различаются, попытка преобразовать их в строку, число или логическое значение.  
  
-   `NaN`не равно к любому другому объекту, включая себя.  
  
-   Отрицательный нуль равен положительному нулю.  
  
-   `null`Оба равно `null` и `undefined`.  
  
-   Значения считаются равными, если они одинаковые строки, эквивалентные числа, одного объекта, идентичные логические значения, или (если различных типов) они могут быть приведены к одной из этих ситуаций.  
  
-   Все прочие сравнения считаются неравными.  
  
 Операторы идентификаторов: `===`,`!==`  
  
 Эти операторы работают так же, как операторы равенства, за исключением того, что преобразование типа не выполняется. Если оба выражения типы не совпадают, эти выражения всегда возвращают `false`.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)