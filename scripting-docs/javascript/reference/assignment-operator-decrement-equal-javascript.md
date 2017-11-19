---
title: "Оператор присваивания (=) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- =
- Assign
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- = operator, about = operator
- = operator, assignment operators
- = operator
- assignment operators, JavaScript
ms.assetid: 1c46a560-ec8d-41c5-a806-30c4843789c4
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1b89e444d55f5a0a05cbb444b182dac27627d9b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="assignment-operator--javascript"></a>Оператор присваивания (=) (JavaScript)
Присваивает значение переменной.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
result = expression  
```  
  
## <a name="parameters"></a>Параметры  
 `result`  
 Любая переменная.  
  
 `expression`  
 Произвольное числовое выражение.  
  
## <a name="remarks"></a>Примечания  
 = Оператор ведет себя как другие операторы, поэтому значение выражения, содержащие его. Это означает, что можно соединить в цепочку операторы присваивания следующим образом: `j = k = l = 0`. В этом случае `j`, `k`, и `l` равны нулю.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)