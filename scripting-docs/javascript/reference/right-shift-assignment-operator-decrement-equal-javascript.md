---
title: Оператор присваивания сдвига вправо (&gt;&gt;=) (JavaScript) | Документы Microsoft
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
- '>>='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '>>= operator [JavaScript]'
- right shift operators [JavaScript]
- assignment operators, JavaScript
ms.assetid: 8c1f7f90-e3ac-42ee-94f2-5ccc47d7aef6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb93d146ad00bd19c09fb4cfca3af776a11f245d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640444"
---
# <a name="right-shift-assignment-operator-gtgt-javascript"></a>Оператор присваивания сдвига вправо (&gt;&gt;=) (JavaScript)
Сдвигает значение переменной вправо на количество битов, указанное в значении выражения, с сохранением знака и присваивает результат переменной.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
result >>= expression  
```  
  
## <a name="parameters"></a>Параметры  
 *результат*  
 Любая переменная.  
  
 *выражение*  
 Любое выражение.  
  
## <a name="remarks"></a>Примечания  
 С помощью  **>>=**  оператор именно эквивалентно следующему выражению:  
  
```JavaScript  
result = result >> expression  
```  
  
 **>>=**  Оператор Сдвигает биты *результат* вправо на количество битов, указанное в *выражение*. Знак бита *результат* используется для заполнения позиций слева. Сдвигаемые право цифры отбрасываются. Например, после вычисления следующего кода *temp* имеет значение -4: 14 (11110010 в двоичном) на два бита вправо получается значение -4 (11111100 в двоичном выражении).  
  
```JavaScript  
var temp  
temp = -14  
temp >>= 2  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор побитового сдвига влево (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Оператор побитового сдвига вправо (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Оператор сдвига вправо без учета знака (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)