---
title: "Метод toUpperCase (String) (JavaScript) | Документы Microsoft"
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
- toUpperCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toUpperCase method
ms.assetid: 4fd4ccc3-e794-498a-9db1-baf48fc1dda1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0b84de440fc9e3cece3b831b57a90be394e819ac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="touppercase-method-string-javascript"></a>Метод toUpperCase (String) (JavaScript)
Преобразует все буквенные символы в строке в верхний регистр.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      strVariable.toUpperCase()  
"String Literal".toUpperCase()   
```  
  
## <a name="remarks"></a>Примечания  
 `toUpperCase` Метод не оказывает влияния на неалфавитных символов.  
  
## <a name="example"></a>Пример  
 В следующем примере демонстрируется влияние `toUpperCase` метод:  
  
```JavaScript  
var str1 = "This is a STRING.";  
var str2 = str1.toUpperCase();  
document.write(str2);  
  
// Output: THIS IS A STRING.  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применяется к**: [строковый объект](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод toLocaleUpperCase (String)](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)   
 [Метод toLowerCase](../../javascript/reference/tolowercase-method-javascript.md)