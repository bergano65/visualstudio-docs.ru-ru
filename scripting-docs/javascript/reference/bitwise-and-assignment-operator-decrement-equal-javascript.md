---
title: Оператор присваивания побитового и (&amp;=) (JavaScript) | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '&='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '&= operator'
- assignment operators, bitwise [JavaScript]
- AND operator
- bitwise operators, AND operator
ms.assetid: e7e2eabb-4fc1-4fdc-9dd8-1e6d715371fa
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dfd2a77e66296cafc6c8403570f0536e1333e081
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634044"
---
# <a name="bitwise-and-assignment-operator-amp-javascript"></a>Оператор присваивания побитового и (&amp;=) (JavaScript)
Задает результат поразрядной операции AND для значения переменной и значения выражения. Переменную и выражение обрабатываются как 32-разрядных целых чисел.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
result &= expression  
```  
  
## <a name="parameters"></a>Параметры  
 `result`  
 Любая переменная.  
  
 `expression`  
 Любое выражение.  
  
## <a name="remarks"></a>Примечания  
 Использование этого оператора является эквивалентно следующему выражению:  
  
```JavaScript  
result = result & expression  
```  
  
 [Оператор побитового и (&)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md) рассматривает двоичное представление значений `result` и `expression` и выполняет побитовую операцию и над ними. Выходные данные этой операции ведет себя следующим образом:  
  
```JavaScript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
expr1 &= expr2;  
  
document.write(expr1);  
```  
  
 Любое время, оба выражения имеют значение 1 в позиции, результат содержит 1 в этой позиции. В противном случае результат имеет значение 0 в этой позиции.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор побитового и (&)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)