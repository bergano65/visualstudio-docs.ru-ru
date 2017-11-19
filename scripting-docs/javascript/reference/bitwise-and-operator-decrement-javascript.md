---
title: "Оператор побитового и (&amp;) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '&'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- assignment operators, bitwise [JavaScript]
- '& operator, about & operator'
- AND operator
- '& operator'
- bitwise operators, AND operator
- '& operator, bitwise operators'
ms.assetid: a8c17a55-2599-4518-98d7-671699f4d5f3
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa8b3eec0cbd7c172d08b16120fb54f3be3c6a48
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-and-operator-amp-javascript"></a>Оператор побитового и (&amp;) (JavaScript)
Выполняет побитовую операцию и над двумя выражениями с 32-разрядной.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
result = expression1 & expression2  
```  
  
## <a name="parameters"></a>Параметры  
 `result`  
 Результат операции.  
  
 `expression1`  
 Любое выражение.  
  
 `expression2`  
 Любое выражение.  
  
## <a name="remarks"></a>Примечания  
 `&` Выполняет операцию побитового и для каждого из битов двух выражений 32-разрядной. Если оба бита равны 1, результат равен 1. В противном случае результат равен 0.  
  
|Bit1|Бит2|Умножение значения|  
|----------|----------|-----------------|  
|0|0|0|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
  
 В следующих примерах показано использование `&` оператор.  
  
```JavaScript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
var result = expr1 & expr2;  
  
document.write(result);  
// Output: 1  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор присваивания побитового и (& =)](../../javascript/reference/bitwise-and-assignment-operator-decrement-equal-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)