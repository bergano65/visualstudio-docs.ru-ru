---
title: "Оператор побитового сдвига вправо (&gt;&gt;) (JavaScript) | Документы Microsoft"
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
- '>>'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '>> operator'
- '>> operator, about >> operator'
- '>> operator, bitsets'
- bitwise operators, right shift operator
ms.assetid: 89dc57e0-0b0d-49a4-a8ed-56d8bb20f3e3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70db0c176b475886a26cfe4c06f7f2f0c9d4fc2a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-right-shift-operator-gtgt-javascript"></a>Оператор побитового сдвига вправо (&gt;&gt;) (JavaScript)
Сдвигает вправо биты выражения, сохраняя знак.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
result = expression1 >> expression2  
```  
  
## <a name="parameters"></a>Параметры  
 *результат*  
 Любая переменная.  
  
 *expression1*  
 Любое выражение.  
  
 *Expression2*  
 Любое выражение.  
  
## <a name="remarks"></a>Примечания  
 >> Оператор Сдвигает биты *expression1* вправо на количество битов, указанное в *expression2*. Знак бита *expression1* используется для заполнения позиций слева. Сдвигаемые право цифры отбрасываются. Например, после вычисления следующего кода *temp* имеет значение -4:-14 (11110010 в двоичной) на два бита вправо получается значение -4 (11111100 выражении в двоичном).  
  
```JavaScript  
var temp  
temp = -14 >> 2  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор побитового сдвига влево (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Оператор присваивания сдвига вправо (>> =)](../../javascript/reference/right-shift-assignment-operator-decrement-equal-javascript.md)   
 [Оператор сдвига вправо без учета знака (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)