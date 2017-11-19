---
title: "Метод SHIFT (Array) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: shift
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: shift method
ms.assetid: f33baec5-f67e-4760-b7c1-553727bd0423
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 664c3f764950b329cea8356f5b350ee917f0a60f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="shift-method-array-javascript"></a>Метод shift (Array) (JavaScript)
Удаляет первый элемент из массива и возвращает его.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
arrayObj.shift( )  
```  
  
#### <a name="parameters"></a>Параметры  
 Необходимая `arrayObj` ссылка `Array` объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает элемент, удаленные из массива.  
  
## <a name="remarks"></a>Примечания  
 В следующем примере показано использование метода `shift`.  
  
```JavaScript  
var arr = new Array(10, 11, 12);  
while (arr.length > 0)  
    {  
    var i = arr.shift();  
    document.write (i.toString() + " ");  
    }  
  
// Output:   
// 10 11 12  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Метод unshift (Array)](../../javascript/reference/unshift-method-array-javascript.md)