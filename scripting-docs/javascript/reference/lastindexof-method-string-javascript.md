---
title: Метод lastIndexOf (строка) (JavaScript) | Документы Microsoft
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
- lastIndexOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- lastIndexOf method, string
- string, lastIndexOf method
ms.assetid: 1ed36ccd-0f0b-4f16-be45-0567207670af
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0fa0f35e970435a4d0296493c20afdeaac128cae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637584"
---
# <a name="lastindexof-method-string-javascript"></a>Метод lastIndexOf (строка) (JavaScript)
Возвращает последнее вхождение подстроки в строке.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
strObj.lastIndexOf(substring[, startindex])  
```  
  
## <a name="parameters"></a>Параметры  
 `strObj`  
 Обязательный. Объект `String` или строковый литерал.  
  
 `substring`  
 Обязательный. Подстрока для поиска.  
  
 `startindex`  
 Необязательно. Индекс, с которой начинается поиск. Если не указано, поиск начинается с конца проверяемой строки.  
  
## <a name="remarks"></a>Примечания  
 **LastIndexOf** метод возвращает целочисленное значение, указывающее начало подстроки в пределах `String` объекта. Если подстрока не найдена, возвращается значение -1.  
  
 Если значение `startindex` отрицательно, то `startindex` рассматривается как ноль. Если оно больше наибольшего индекса положения знака, оно рассматривается как наибольший возможный индекс.  
  
 Поиск выполняется начиная с последнего символа в строке. В противном случае этот метод идентичен **indexOf**.  
  
 Следующий пример иллюстрирует использование **lastIndexOf** метод.  
  
```JavaScript  
var str = "time, time";  
  
var s = "";  
s += "time is at position " + str.lastIndexOf("time");  
s += "<br />";  
s += "abc is at position " + str.lastIndexOf("abc");  
  
document.write(s);  
  
// Output:  
// time is at position 6  
// abc is at position -1  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применяется к**: [строковый объект](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод indexOf (строка)](../../javascript/reference/indexof-method-string-javascript.md)