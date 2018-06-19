---
title: Функция Math.ABS (JavaScript) | Документы Microsoft
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
- abs
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- absolute values, calculating
- absolute values
- numeric expressions
- abs method
ms.assetid: 9af4b5b8-de77-47bb-bb59-abdde371e4c3
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5719905a7de375f1b409378f0579e3d8b25209fc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638374"
---
# <a name="mathabs-function-javascript"></a>Функция Math.abs (JavaScript)
Возвращает абсолютное значение числа (значение без учета положительное или отрицательное). Например абсолютное значение -5 является таким же, как абсолютное значение 5.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Math.abs(number)  
```  
  
#### <a name="parameters"></a>Параметры  
 Необходимая `number` аргумент является числовым выражением, для которого требуется абсолютное значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Абсолютное значение `number` аргумент.  
  
## <a name="example"></a>Пример  
 В следующем примере показано применение функции `abs`.  
  
```JavaScript  
var s;  
var v1 = Math.abs(6);  
var v2 = Math.abs(-6);  
if (v1 == v2) {  
    document.write("Absolute values are the same.");  
}  
else {  
document.write("Absolute values are different.");  
}  
  
// Output: Absolute values are the same.  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применяется к**: [объект Math](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Объект Math](../../javascript/reference/math-object-javascript.md)