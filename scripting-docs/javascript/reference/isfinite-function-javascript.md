---
title: Функция isFinite (JavaScript) | Документы Microsoft
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
- isFinite
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- finite numbers
- isFinite method
ms.assetid: ea9287d2-892f-496b-86b7-f9196868d5cf
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce78afe59190a03fb079841e7691f84c01eebedd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637004"
---
# <a name="isfinite-function-javascript"></a>Функция isFinite (JavaScript)
Определяет, является ли предоставленное число конечным.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
isFinite(number)   
```  
  
## <a name="remarks"></a>Примечания  
 Необходимая `number` аргумент — любое числовое значение.  
  
 `isFinite` Возврата функцией `true` Если `number` имеет любое значение, отличное от `NaN`, отрицательной бесконечностью или плюс бесконечность. В этих трех случаях он возвращает **false**.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применяется к**: [глобального объекта](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Функция isNaN](../../javascript/reference/isnan-function-javascript.md)