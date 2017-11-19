---
title: "Оператор присваивания сдвига влево (&lt;&lt;=) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: <<=
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- <<= operator [JavaScript]
- left shift assignment operator (<<=) [JavaScript]
- left shift operators [JavaScript]
- assignment operators, JavaScript
ms.assetid: 9f30ff46-48cc-4931-b260-edef31ff0076
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf00545947f6a84f99c519fcbed887b84c179fb5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="left-shift-assignment-operator-ltlt-javascript"></a>Оператор присваивания сдвига влево (&lt;&lt;=) (JavaScript)
Перемещает указанное число битов влево и присваивает результат для `result`. Операция, освобожденные биты заполняются 0.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
result <<= expression  
```  
  
## <a name="parameters"></a>Параметры  
 `result`  
 Любая переменная.  
  
 `expression`  
 Число битов для перемещения.  
  
## <a name="remarks"></a>Примечания  
 С помощью `<<=` оператором является тот же`result = result << expression`  
  
 В следующем примере показано использование оператора `<<=`.  
  
```JavaScript  
// 14 is 00000000000000000000000000001110  
var temp = 14;  
temp <<= 2;   
document.write(temp);  
// 56 is 00000000000000000000000000111000  
Output: 56  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор побитового сдвига влево (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Оператор побитового сдвига вправо (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Оператор сдвига вправо без учета знака (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)