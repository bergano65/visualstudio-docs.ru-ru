---
title: Оператор побитового сдвига влево (&lt;&lt;) (JavaScript) | Документы Microsoft
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
- <<
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- << operator
- left shift operators
- << operator, about << operator
- bitwise operators, Left Shift operator
ms.assetid: 18148596-7b86-4add-aeef-106991c69435
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d63fc50659695f518e581edbed67c009b36577f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634214"
---
# <a name="bitwise-left-shift-operator-ltlt-javascript"></a>Оператор побитового сдвига влево (&lt;&lt;) (JavaScript)
Сдвигает биты выражения влево.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
result = expression1 << expression2  
```  
  
## <a name="parameters"></a>Параметры  
 *результат*  
 Любая переменная.  
  
 *expression1*  
 Любое выражение.  
  
 *Expression2*  
 Любое выражение.  
  
## <a name="remarks"></a>Примечания  
 **<<**  Оператор Сдвигает биты *expression1* влево на количество битов, указанное в *expression2*. Пример:  
  
```JavaScript  
var temp  
temp = 14 << 2  
```  
  
 Переменная *temp* имеет значение 56, так как 14 (00001110 в двоичном выражении) на два бита влево получается значение 56 (00111000 в двоичном выражении).  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор присваивания сдвига влево (<\<=)](../../javascript/reference/left-shift-assignment-operator-decrement-equal-javascript.md)   
 [Оператор побитового сдвига вправо (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Оператор сдвига вправо без учета знака (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)