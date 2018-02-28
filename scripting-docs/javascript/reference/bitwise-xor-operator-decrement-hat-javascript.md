---
title: "Оператор побитового исключающего или (^) (JavaScript) | Документы Microsoft"
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
- ^
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- bitwise operators, XOR operator
- XOR operator
ms.assetid: 44ef0d18-abb5-4d83-9e77-6394635b3f48
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ebe8ff9805793bf306688622b0b29007b1562e2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-xor-operator--javascript"></a>Оператор побитового исключающего ИЛИ (^) (JavaScript)
Выполняет операцию побитового исключающего ИЛИ для двух выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
result = expression1 ^ expression2  
```  
  
## <a name="parameters"></a>Параметры  
 *результат*  
 Любая переменная.  
  
 *expression1*  
 Любое выражение.  
  
 *Expression2*  
 Любое выражение.  
  
## <a name="remarks"></a>Примечания  
 **^**  Оператор рассматривает двоичное представление значений двух выражений и выполняет над ними операцию побитового исключающего или. В результате этой операции ведет себя следующим образом:  
  
```JavaScript  
0101   (expression1)  
1100   (expression2)  
----  
1001   (result)  
```  
  
 Если одно и только одно из выражений имеет значение 1 в цифра, результат имеет значение 1 в этой позиции. В противном случае результат имеет значение 0 в этой позиции.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор присваивания побитового исключающего или (^ =)](../../javascript/reference/bitwise-xor-assignment-operator-decrement-hat-equal-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)