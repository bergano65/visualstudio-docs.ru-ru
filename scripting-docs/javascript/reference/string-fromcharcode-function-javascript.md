---
title: "Функция String.fromCharCode (JavaScript) | Документы Microsoft"
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
- fromCharCode
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- fromCharCodeAt method
- characters, from Unicode
ms.assetid: f64120c1-23a7-48ca-8d1c-db3e8856cab4
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbcd9062d7da0b73647c1d9eb6cc207af23c3532
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="stringfromcharcode-function-javascript"></a>Функция String.fromCharCode (JavaScript)
Возвращает строку, содержащую набор значений знаков Юникода.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
String.fromCharCode([code1[, code2[, ...[, codeN]]]])   
```  
  
## <a name="parameters"></a>Параметры  
 `String`  
 Обязательный. Объект `String`.  
  
 `code1`, . . . , `codeN`  
 Необязательно. Набор значений знаков Юникода для преобразования в строку. Если аргументы не указаны, результатом является пустой строкой.  
  
## <a name="remarks"></a>Примечания  
 Вызовите эту функцию `String` объекта, а не на экземпляр string.  
  
 В следующем примере показано, как с помощью этого метода:  
  
```JavaScript  
var test = String.fromCharCode(112, 108, 97, 105, 110);  
document.write(test);  
  
// Output: plain  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Метод charCodeAt (String)](../../javascript/reference/charcodeat-method-string-javascript.md)