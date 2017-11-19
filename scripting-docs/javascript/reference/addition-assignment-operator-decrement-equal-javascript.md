---
title: "Оператор присваивания сложения (+=) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: +=
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- addition assignment operator (+=)
- += operator
- assignment operators, JavaScript
ms.assetid: 8517d05c-38b0-4107-bea4-253eb420f438
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38d86c537dda90dd7f44923b97384b3609dad5ba
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="addition-assignment-operator--javascript"></a>Оператор присваивания сложения (+=) (JavaScript)
Прибавляет значение выражения к значению переменной и присваивает результат переменной.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
result += expression   
```  
  
## <a name="parameters"></a>Параметры  
 `result`  
 Любая переменная.  
  
 `expression`  
 Любое выражение.  
  
## <a name="remarks"></a>Примечания  
 Использование этого оператора именно тот же: `result = result + expression`.  
  
 Типы двух выражений определяют поведение `+=` оператор.  
  
|If|Следующее действие|  
|--------|----------|  
|Оба выражения имеют числовые или логические|Добавить|  
|Оба выражения представляют собой строки|Объединение|  
|Одно выражение является числовым, а второе — строка.|Объединение|  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор сложения (+)](../../javascript/reference/addition-operator-decrement-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)