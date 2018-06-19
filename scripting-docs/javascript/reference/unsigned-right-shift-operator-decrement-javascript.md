---
title: Оператор сдвига вправо без учета знака (&gt;&gt;&gt;) (JavaScript) | Документы Microsoft
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
- '>>>'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- unsigned right shift operator (>>>)
- '>>> operator'
ms.assetid: df48bdfc-8741-46ab-b681-449da57ac95c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: efb873bedc0a64089c7ec892d6378b4869c0ca21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641644"
---
# <a name="unsigned-right-shift-operator-gtgtgt-javascript"></a>Оператор сдвига вправо без учета знака (&gt;&gt;&gt;) (JavaScript)
Сдвигает вправо биты выражения, не сохраняя знака.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
result = expression1 >>> expression2  
```  
  
## <a name="parameters"></a>Параметры  
 *результат*  
 Любая переменная.  
  
 *expression1*  
 Любое выражение.  
  
 *Expression2*  
 Любое выражение.  
  
## <a name="remarks"></a>Примечания  
 **>>>**  Оператор Сдвигает биты *expression1* вправо на количество битов, указанное в *expression2*. Добавляются нули слева. Сдвигаемые право цифры отбрасываются. Пример:  
  
```JavaScript  
var temp  
temp = -14 >>> 2  
```  
  
 Переменная *temp* начальное значение -14 (11111111 11111111 11111111 11110010 в двоичном дополнение двух). При это два бита сдвигаются вправо получается значение 1073741820 (00111111 11111111 11111111 11111100 в двоичном выражении).  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор присваивания сдвига вправо без учета знака (>>> =)](../../javascript/reference/unsigned-right-shift-assignment-operator-decrement-equal-javascript.md)   
 [Оператор побитового сдвига влево (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Оператор побитового сдвига вправо (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)