---
title: "Побитовый оператор не (~) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ~
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- NOT operator
- bitwise operators, NOT operator
ms.assetid: 39f92474-fe05-4a8b-9ad8-caca93f82bca
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aec64b055b260efb7a4b0d952aed9b3a5d7ddc82
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-not-operator--javascript"></a>Оператор побитового НЕ (~) (JavaScript)
Выполняет операцию побитового НЕ (отрицания) для выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
result = ~ expression  
```  
  
## <a name="parameters"></a>Параметры  
 *результат*  
 Любая переменная.  
  
 *выражение*  
 Любое выражение.  
  
## <a name="remarks"></a>Примечания  
 Все унарные операторы, такие как `~` вычисляют выражения следующим образом:  
  
-   Если применяется не определен или `null` возникает выражения, ошибка времени выполнения.  
  
-   Объекты преобразуются в строки.  
  
-   Строки преобразуются в числа, если это возможно. В противном случае возникает ошибка времени выполнения.  
  
-   Логические значения обрабатываются как числа (0, если значение равно false, 1, если значение true).  
  
 Оператор применяется к результирующему числу.  
  
 `~` Оператор рассматривает двоичное представление значений выражения и выполняет операцию побитового отрицания на нем.  
  
 Любая цифра, равного 1 в выражении становится равной нулю в результат. Любая цифра с 0 в выражении становится 1 в результате.  
  
 В следующем примере показано использование побитового не (~)-оператор.  
  
```  
var temp = ~5;  
```  
  
 Результирующее значение равно -6, как показано в следующей таблице.  
  
|Выражение|Двоичное значение (дополнение двух)|Десятичное значение|  
|----------------|---------------------------------------|-------------------|  
|5|00000000 00000000 00000000 00000101|5|  
|~5|11111111 11111111 11111111 11111010|-6|  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Логический оператор не (!)](../../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)