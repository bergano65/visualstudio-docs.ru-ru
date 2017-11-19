---
title: "Оператор присваивания побитового исключающего или (^ =) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ^=
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ^= operator, about ^= operator
- assignment operators, bitwise [JavaScript]
- bitwise operators, XOR operator
- XOR operator
- ^= operator
ms.assetid: a6ded216-27b6-4fc4-a51b-7d10cc6f820c
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 511ff5b3346bb2b04bf4c24cb3e0b715b2ccf4c5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-xor-assignment-operator--javascript"></a>Оператор присваивания побитового исключающего ИЛИ (^=) (JavaScript)
Выполняет операцию побитового исключающего ИЛИ для значения переменной и значения выражения, а затем присваивает результат переменной.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
result ^= expression  
```  
  
## <a name="parameters"></a>Параметры  
 *результат*  
 Любая переменная.  
  
 *выражение*  
 Любое выражение.  
  
## <a name="remarks"></a>Примечания  
 С помощью  **^=**  оператор именно эквивалентно следующему выражению:  
  
```JavaScript  
result = result ^ expression  
```  
  
 **^=**  Оператор рассматривает двоичное представление значений двух выражений и выполняет над ними операцию побитового исключающего или. В результате этой операции ведет себя следующим образом:  
  
```JavaScript  
0101    (result)  
1100    (expression)  
----  
1001    (result)  
```  
  
 Если одно и только одно из выражений имеет значение 1 в цифра, результат имеет значение 1 в этой позиции. В противном случае результат имеет значение 0 в этой позиции.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор побитового исключающего или (^)](../../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)