---
title: Метод Repeat (String) (JavaScript) | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: fe02cdfd-f0f6-45a2-ad36-31c4300ef142
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1a3d6edce877a97b0e46a69c43b667231c26981
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638714"
---
# <a name="repeat-method-string-javascript"></a>Метод repeat (String) (JavaScript)
Возвращает новый объект string со значением, равным исходной строке, повторенной указанное число раз.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
stringObj.repeat(count);  
```  
  
#### <a name="parameters"></a>Параметры  
 `stringObj`  
 Обязательный. Строковый объект.  
  
 `count`  
 Обязательный. Число повторений исходной строки в возвращаемой строке.  
  
## <a name="exceptions"></a>Исключения  
 Этот метод вызывает ошибку RangeError только в том случае, если аргумент представляет собой отрицательное число или +бесконечность.  
  
## <a name="remarks"></a>Примечания  
 Метод `repeat` объединяет исходную и новую строку столько раз, сколько указывает параметр `count`.  
  
 Этот метод вызывает ошибку, если `count` — не положительное число меньше `Infinity`.  
  
## <a name="example"></a>Пример  
  
```JavaScript  
"abc".repeat(3); // Returns "abcabcabc"  
"abc".repeat(0); // Returns an empty string.  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]