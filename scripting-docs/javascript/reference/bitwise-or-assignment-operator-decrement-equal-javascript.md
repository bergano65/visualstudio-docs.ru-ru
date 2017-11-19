---
title: "Побитовый оператор назначения или (| =) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '|='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- assignment operators, bitwise [JavaScript]
- '|= operator'
- bitwise operators, OR operator
- OR operator
ms.assetid: 9b424ff6-4442-4621-b3b6-83e7fd1e5cd5
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ce9cadcf07906c9eba6749706620ae6293c2682
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-or-assignment-operator--javascript"></a>Оператор присваивания побитового ИЛИ (|=) (JavaScript)
Выполняет операцию побитового ИЛИ для значения переменной и значения выражения, а затем присваивает результат переменной.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
result |= expression  
```  
  
## <a name="parameters"></a>Параметры  
 *результат*  
 Любая переменная.  
  
 *выражение*  
 Любое выражение.  
  
## <a name="remarks"></a>Примечания  
 Использование этого оператора именно эквивалентно следующему выражению:  
  
```JavaScript  
result = result | expression  
```  
  
 **&#124; =** оператор рассматривает двоичное представление значений *результат* и *выражение* и выполняет операцию побитового OR над ними. В результате этой операции ведет себя следующим образом:  
  
```JavaScript  
0101    (result)  
1100    (expression)  
----  
1101    (output)  
```  
  
 Каждый раз, либо из выражений имеет значение 1 в цифра, результат имеет значение 1 в этой позиции. В противном случае результат имеет значение 0 в этой позиции.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Побитовый оператор или оператор (&#124;)](../../javascript/reference/bitwise-or-operator-decrement-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)