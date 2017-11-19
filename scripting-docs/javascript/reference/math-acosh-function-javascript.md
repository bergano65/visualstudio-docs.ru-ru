---
title: "Функция Math.ACOSH (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 881dd2a0-36a5-403b-a3dc-523d8e1e1317
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1fd75140dfcf3d9ac703c2aeadf68bea4da9e0dc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="mathacosh-function-javascript"></a>Функция Math.acosh (JavaScript)
Возвращает гиперболический арккосинус (или обратный гиперболический косинус) числа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Math.acosh(number)  
```  
  
#### <a name="parameters"></a>Параметры  
 Обязательный аргумент `number` является числовым выражением.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Обратный гиперболический косинус аргумента `number` в радианах.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано, как использовать функцию `acosh`.  
  
```JavaScript  
var v1 = Math.acosh(3);  
vary v2 = Math.acosh(-1);  
  
document.write(v1);  
document.write("</br>");  
document.write(v2);  
  
// Output:  
// 1.762747174039086  
// NaN  
  
```  
  
## <a name="remarks"></a>Примечания  
 **Применяется к**: [объект Math](../../javascript/reference/math-object-javascript.md)  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Функция Math.ACOS](../../javascript/reference/math-acos-function-javascript.md)   
 [Функция Math.ASIN](../../javascript/reference/math-asin-function-javascript.md)   
 [Функция Math.ATAN](../../javascript/reference/math-atan-function-javascript.md)   
 [Функция Math.cos](../../javascript/reference/math-cos-function-javascript.md)   
 [Функция Math.sin](../../javascript/reference/math-sin-function-javascript.md)   
 [Функция Math.tan](../../javascript/reference/math-tan-function-javascript.md)   
 [Объект Math](../../javascript/reference/math-object-javascript.md)