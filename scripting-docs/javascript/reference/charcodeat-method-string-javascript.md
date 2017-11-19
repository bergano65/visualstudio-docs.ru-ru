---
title: "Метод charCodeAt (String) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: charCodeAt
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: charCodeAt method
ms.assetid: 5b0290a7-ee4d-4738-a909-c02ef64a2f1a
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e7b8e62dfd29aa42d9816d0c5e27cc90440751a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="charcodeat-method-string-javascript"></a>Метод charCodeAt (String) (JavaScript)
Возвращает значение Юникода символа в указанном месте.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
strObj. charCodeAt(index)  
```  
  
## <a name="parameters"></a>Параметры  
 `strObj`  
 Обязательный. Любой `String` или строковый литерал.  
  
 `index`  
 Обязательный. Отсчитываемый от нуля индекс требуемого символа. Если нет никакого символа по указанному индексу `NaN` возвращается.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода `charCodeAt`.  
  
```JavaScript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";   
document.write(str.charCodeAt(str.length - 1));  
  
// Output: 90   
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Функция String.fromCharCode](../../javascript/reference/string-fromcharcode-function-javascript.md)