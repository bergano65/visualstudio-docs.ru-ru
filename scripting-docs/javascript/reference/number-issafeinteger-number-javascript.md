---
title: Функция Number.isSafeInteger (Number) (JavaScript) | Документы Microsoft
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
ms.assetid: c7ef6ce8-fe71-4e53-be44-4dd440aef21d
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eebc2147bc5043341be7e883548af825922036f9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638354"
---
# <a name="numberissafeinteger-number-javascript"></a>Number.isSafeInteger (Number) (JavaScript)
Возвращает логическое значение, указывающее, можно ли безопасно представить число в JavaScript.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Number.isSafeInteger(numValue)   
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 `true`, если число находится в диапазоне от `Number.MIN_SAFE_INTEGER` до `Number.MAX_SAFE_INTEGER` включительно; в противном случае — `false`.  
  
## <a name="remarks"></a>Примечания  
 В JavaScript безопасное целое число — это число двойной точности IEEE 754 до округления.  
  
## <a name="example"></a>Пример  
  
```JavaScript  
// Returns true  
Number.isSafeInteger(-100)  
Number.isSafeInteger(9007199254740991)  
  
// Returns false  
Number.isSafeInteger(Number.NaN)  
Number.isSafeInteger(Infinity)  
Number.isSafeInteger("100")  
Number.isSafeInteger(9007199254740992);  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Применяется к**: [число объектов](../../javascript/reference/number-object-javascript.md)