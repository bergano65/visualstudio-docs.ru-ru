---
title: Метод Search (String) (JavaScript) | Документы Microsoft
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
- search
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- search method
ms.assetid: 1cae0fbc-3319-4327-ba4e-d5fa2c4a9ba0
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 730fb1604147b56fc5ab1e312bf7a6dfb5487a5a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639734"
---
# <a name="search-method-string-javascript"></a>Метод search (String) (JavaScript)
Находит первое совпадение подстроки в поиске регулярного выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
stringObj.search(rgExp)   
```  
  
## <a name="parameters"></a>Параметры  
 `stringObj`  
 Обязательный. `String` Или строковый литерал, в котором выполняется поиск.  
  
 `rgExp`  
 Обязательный. Экземпляр **регулярное выражение** объект, содержащий шаблон регулярного выражения и установленные флаги.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если соответствие найдено, **поиска** метод возвращает целочисленное значение, которое указывает смещение от начала строки, в которой произошло первое совпадение. Если совпадение не найдено, возвращается значение -1.  
  
## <a name="remarks"></a>Примечания  
 Можно также задать `i` флаг, который вызывает поиска без учета регистра.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование **поиска** метод.  
  
```JavaScript  
var src = "is but a Dream within a dream";  
var re = /dream/;  
var pos = src.search(re);  
document.write(pos);  
document.write("<br/>");  
  
re = /dream/i;  
pos = src.search(re);  
document.write(pos);  
  
// Output:   
// 24   
// 9  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применяется к**: [строковый объект](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод exec (Regular Expression)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [Метод Match (String)](../../javascript/reference/match-method-string-javascript.md)   
 [Объект регулярного выражения](../../javascript/reference/regular-expression-object-javascript.md)   
 [Синтаксис регулярного выражения (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Метод replace (строка)](../../javascript/reference/replace-method-string-javascript.md)   
 [Метод Test (Regular Expression)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Программирование регулярных выражений (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)