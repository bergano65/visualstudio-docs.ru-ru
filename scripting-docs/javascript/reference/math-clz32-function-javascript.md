---
title: "Функция Math.clz32 (JavaScript) | Документы Microsoft"
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
ms.assetid: 34615d7a-6d88-4ab5-a696-7e496caa51db
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 511f407acc327a32ed6c53c12283503e20b514fe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="mathclz32-function-javascript"></a>Функция Math.clz32 (JavaScript)
Возвращает число начальных нулей в 32-разрядном двоичном представлении числа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Math.clz32(  
number  
)   
```  
  
## <a name="remarks"></a>Примечания  
 Если значение `number` равно 0, результат будет 32. Если самый значимый бит 32-разрядной двоичной кодировки `number` равен 1, результат будет 0.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Применяется к**: [объект Math](../../javascript/reference/math-object-javascript.md)