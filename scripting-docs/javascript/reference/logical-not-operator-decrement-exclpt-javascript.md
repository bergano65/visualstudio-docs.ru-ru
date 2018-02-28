---
title: "Логический оператор не (!) (JavaScript) | Документы Microsoft"
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
- '!'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Logical NOT operator
- '! operator'
- '! operator, about ! operator'
ms.assetid: 68c3dc71-ae95-4293-9155-67405846d71d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29c27b9cd670989eb2112de5067e68bd09d76903
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="logical-not-operator--javascript"></a>Оператор логического НЕ (!) (JavaScript)
Выполняет логическое отрицание выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
result = !expression  
```  
  
## <a name="parameters"></a>Параметры  
 *результат*  
 Любая переменная.  
  
 *выражение*  
 Любое выражение.  
  
## <a name="remarks"></a>Примечания  
 В следующей таблице показано, как *результат* определяется.  
  
|Если `expression` является|Затем `result` —|  
|------------------------|----------------------|  
|True|False|  
|False|True|  
  
 Все унарные операторы, такие как **!** вычисляют выражения следующим образом:  
  
-   Если применяется не определен или `null` возникает выражения, ошибка времени выполнения.  
  
-   Объекты преобразуются в строки.  
  
-   Строки преобразуются в числа, если это возможно. В противном случае возникает ошибка времени выполнения.  
  
-   Логические значения обрабатываются как числа (0, если значение равно false, 1, если значение true).  
  
 Оператор применяется к результирующему числу.  
  
 Для **!** оператор, если *выражение* отлично от нуля, *результат* равно нулю. Если *выражение* равен нулю, *результат* -1.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Побитовый оператор не (~)](../../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)