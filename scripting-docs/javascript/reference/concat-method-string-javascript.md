---
title: Метод concat (строка) (JavaScript) | Документы Microsoft
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
- concat
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- concat method (String)
- Concat method
ms.assetid: 5d28ebb2-d534-4179-9297-a4c821ee9f24
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b6419cc6404e06fc780802a30a3b4add8320881
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634004"
---
# <a name="concat-method-string-javascript"></a>Метод concat (строка) (JavaScript)
Возвращает строку, содержащую объединение двух или более строк.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
string1. concat([string2[, string3[, . . . [, stringN]]]])  
```  
  
## <a name="parameters"></a>Параметры  
 `string1`  
 Обязательный. `String` Или строковый литерал, к которому все остальные указано, строки сцепляются.  
  
 `string2,. . ., stringN`  
 Необязательно. Строки, которые следует добавить в конец `string1`.  
  
## <a name="remarks"></a>Примечания  
 Результат `concat` метод эквивалентен: `result`  =  `string1`  +  `string2`  +  `string3`  +  `stringN`. Изменение значения в исходной или результирующей строке не влияет на значение в другой строке. Если какие-либо аргументы не являются строками, они сначала преобразуются в строки перед объединением с `string1`.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование `concat` метода при использовании со строкой:  
  
```JavaScript  
var str1 = "ABCD"  
var str2 = "EFGH";  
var str3 = "1234";  
var str4 = "5678";  
document.write(str1.concat(str2, str3, str4));  
  
// Output: "ABCDEFGH12345678"  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применяется к**: [строковый объект](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Оператор сложения (+)](../../javascript/reference/addition-operator-decrement-javascript.md)