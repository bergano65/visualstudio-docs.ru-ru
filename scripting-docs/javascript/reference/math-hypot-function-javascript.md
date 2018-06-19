---
title: Функция Math.hypot (JavaScript) | Документы Microsoft
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
ms.assetid: 31488f5a-2230-4114-911e-b6d854c7b0a0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a66c0b082356b8dde3f51f739c130378d694f3b4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638264"
---
# <a name="mathhypot-function-javascript"></a>Функция Math.hypot (JavaScript)
Возвращает квадратный корень из суммы квадратов аргументов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Math.hypot ( value1[, value2[, ...values] );  
```  
  
#### <a name="parameters"></a>Параметры  
 `value1`  
 Обязательный. Первое число.  
  
 `value2`  
 Необязательно. Второе число.  
  
 `values`  
 Необязательно. Одно или несколько чисел.  
  
## <a name="remarks"></a>Примечания  
 Если один из аргументов имеет значение NaN, функция возвращает значение NaN. Если аргументы не указаны, функция возвращает значение 0.  
  
## <a name="example"></a>Пример  
 Ниже приведен пример использования функции `Math.hypot`.  
  
```JavaScript  
Math.hypot(3, 4);  
// Returns 5  
  
Math.hypot(3, "4");  
// Returns 5  
  
Math.hypot(3, "four");  
// Returns NaN   
  
Math.hypot(3, 4, 10);  
// Returns 11.180339887498949  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]