---
title: "Функция Math.ACOS (JavaScript) | Документы Microsoft"
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
- acos
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- acos method
- arcosine method
ms.assetid: 828cb3c3-bdf7-4bb7-97ae-3617ce4b2d62
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 773499287e215fbc161f289954811d3ef62bcba6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="mathacos-function-javascript"></a>Функция Math.acos (JavaScript)
Возвращает арккосинус (или обратный косинус) числа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Math.acos(number)  
```  
  
#### <a name="parameters"></a>Параметры  
 Обязательный аргумент `number` является числовым выражением.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Арккосинус параметра `number` аргумент в радианах.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано, как использовать функцию `acos`.  
  
```JavaScript  
var v1 = Math.acos(-1.0);  
var v2 = Math.cos(-1.0);  
  
document.write(v1);  
document.write("<br/>");  
document.write(v2);  
  
// Output:  
// 3.141592653589793  
// 0.5403023058681398  
  
```  
  
## <a name="remarks"></a>Примечания  
 **Применяется к**: [объект Math](../../javascript/reference/math-object-javascript.md)  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Функция Math.ASIN](../../javascript/reference/math-asin-function-javascript.md)   
 [Функция Math.ATAN](../../javascript/reference/math-atan-function-javascript.md)   
 [Функция Math.cos](../../javascript/reference/math-cos-function-javascript.md)   
 [Функция Math.sin](../../javascript/reference/math-sin-function-javascript.md)   
 [Функция Math.tan](../../javascript/reference/math-tan-function-javascript.md)   
 [Объект Math](../../javascript/reference/math-object-javascript.md)