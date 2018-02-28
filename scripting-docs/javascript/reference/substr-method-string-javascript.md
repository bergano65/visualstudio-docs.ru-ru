---
title: "Метод substr (String) (JavaScript) | Документы Microsoft"
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
- substr
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- substr method
ms.assetid: f12541c1-2623-482e-941d-2e22bc3c4a4a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b002bfefbeb81c534c882fa4a4720c93ccca185
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="substr-method-string-javascript"></a>Метод substr (String) (JavaScript)
Возвращает подстроку, начиная с версии в указанном месте и с указанной длины.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
stringvar.substr(start [, length ])   
```  
  
## <a name="parameters"></a>Параметры  
 `stringvar`  
 Обязательный. Строковый литерал или `String` объекта, из которой извлекается подстрока.  
  
 `start`  
 Обязательный. Начальная позиция извлекаемой подстроки. Индекс первого символа в строке равен нулю.  
  
 `length`  
 Необязательно. Число символов для включения в возвращаемой подстроки.  
  
## <a name="remarks"></a>Примечания  
 Если `length` равно нулю или отрицательное значение, возвращается пустая строка. Если не указан, подстрока продолжается до конца `stringvar`.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода `substr`.  
  
```JavaScript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substr(10, 5);    
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10);  
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10, -5);  
document.write("[" + ss + "] <br>");  
  
// Output:  
// [brown]   
// [brown fox jumps over the lazy dog.]   
// []  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применяется к**: [строковый объект](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод substring (String)](../../javascript/reference/substring-method-string-javascript.md)