---
title: Метод SUBSTRING (String) (JavaScript) | Документы Microsoft
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
- substring
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- substrings
- substring method
ms.assetid: 9cf9a005-cbe3-42fd-828b-57a39f54224c
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 15ebaadc7b24fa97f531a22f6deb1453ff52b3e7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640934"
---
# <a name="substring-method-string-javascript"></a>Метод substring (String) (JavaScript)
Возвращает подстроку, расположенную в указанном месте `String` объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      strVariable. substring(start [, end])  
"String Literal".substring(start [, end])   
```  
  
## <a name="parameters"></a>Параметры  
 `start`  
 Обязательный. Отсчитываемый от нуля индекс целочисленное значение, указывающее начало подстроки.  
  
 `end`  
 Необязательно. Отсчитываемый от нуля индекс целочисленное значение, указывающее, конец подстроки. Подстрока включает символы до, но не включая знак обозначается `end`.  
  
 Если `end` опущен, символы от `start` до конца исходной строки возвращаются.  
  
## <a name="remarks"></a>Примечания  
 `substring` Метод возвращает строку, содержащую подстроку из `start` , но не включающую, `end`.  
  
 **Подстроки** метод использует наименьшее значение `start` и `end` в качестве начальной позиции подстроки. Например, strvar.substring (0, 3 **)** и strvar.substring (3, 0) возвращают одну подстроку.  
  
 Если параметр `start` или `end` — `NaN` или отрицательное значение, оно будет заменено ноль.  
  
 Длина подстроки равна абсолютное значение разницы между `start` и `end`. Например возвращается длина подстроки в strvar.substring (0, 3) и strvar.substring (3, 0), равно трем.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование **подстроки** метод.  
  
```JavaScript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substring(10, 15);  
document.write(ss);  
  
// Output:  
// brown  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Метод substr (String)](../../javascript/reference/substr-method-string-javascript.md)