---
title: Оператор присваивания сдвига вправо без учета знака (&gt;&gt;&gt;=) (JavaScript) | Документы Microsoft
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
- '>>>='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '>>>= operator'
- unsigned right shift assignment operator (>>>=)
- assignment operators, JavaScript
ms.assetid: f67c3737-7d39-41ae-9c11-8b16d38f6179
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1272cbb58645df605743c6790642cd0e295442aa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641394"
---
# <a name="unsigned-right-shift-assignment-operator-gtgtgt-javascript"></a>Оператор присваивания сдвига вправо без учета знака (&gt;&gt;&gt;=) (JavaScript)
Сдвигает значение переменной вправо на количество битов, указанное в значении выражения, без сохранения знака и присваивает результат переменной.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
result >>>= expression  
```  
  
## <a name="parameters"></a>Параметры  
 *результат*  
 Любая переменная.  
  
 *выражение*  
 Любое выражение.  
  
## <a name="remarks"></a>Примечания  
 С помощью >>> = оператор совпадает следующим образом:  
  
```JavaScript  
result = result >>> expression  
```  
  
 **>>>=**  Оператор Сдвигает биты *результат* вправо на количество битов, указанное в *выражение*. Добавляются нули слева. Сдвигаемые право цифры отбрасываются. Пример:  
  
```JavaScript  
var temp  
temp = -14  
temp >>>= 2  
```  
  
 Переменная *temp* начальное значение от -14 (11111111 11111111 11111111 11110010 в двоичном дополнение двух). При сдвиге вправо два бита, получается значение 1073741820 (00111111 11111111 11111111 11111100 в двоичном выражении).  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор сдвига вправо без учета знака (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Оператор побитового сдвига влево (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Оператор побитового сдвига вправо (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)