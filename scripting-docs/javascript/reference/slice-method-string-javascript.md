---
title: "Метод slice (строка) (JavaScript) | Документы Microsoft"
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
- slice
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strings [Visual Studio], returning characters
- slice method
ms.assetid: 80cd77a6-3718-492e-8e96-f909d8721d91
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1baa0a05a2d6aa8c06cc962761c8e557632d034c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="slice-method-string-javascript"></a>Метод slice (String) (JavaScript)
Возвращает фрагмент строки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
stringObj.slice(start, [end])   
```  
  
## <a name="parameters"></a>Параметры  
 `stringObj`  
 Обязательный. Объект `String` или строковый литерал.  
  
 `start`  
 Обязательный. Индекс начала указанного фрагмента `stringObj`.  
  
 `end`  
 Необязательно. Индекс в конец заданную часть `stringObj`. Подстрока включает символы до, но не включая знак обозначается `end`. Если это значение не задано, подстрока продолжается до конца `stringObj`.  
  
## <a name="remarks"></a>Примечания  
 `slice` Возвращает `String` объект, содержащий указанную часть `stringObj`.  
  
 `slice` Метод копирует, но не включающую, символе, обозначенном `end`.  
  
 Если `start` имеет отрицательное значение, он рассматривается как *длина*  +  `start` где *длина* длина строки. Если `end` имеет отрицательное значение, он рассматривается как *длина* + `end`. Если `end` — этот параметр опущен, копирование продолжается до конца `stringObj`. Если `end` предшествует `start`, никакие символы копируются в новую строку.  
  
## <a name="example"></a>Пример  
 В первом примере `slice` метод возвращает всю строку. Во втором примере `slice` метод возвращает всю строку, за исключением последнего символа.  
  
```JavaScript  
var str1 = "all good boys do fine";  
  
var slice1 = str1.slice(0);  
var slice2 = str1.slice(0,-1);  
var slice3 = str1.slice(4);  
var slice4 = str1.slice(4, 8);  
  
document.write(slice1 + "<br/>");  
document.write(slice2 + "<br/>");  
document.write(slice3 + "<br/>");  
document.write(slice4);  
  
// Output:  
// all good boys do fine  
// all good boys do fin  
// good boys do fine  
// good  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применяется к**: [строковый объект](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод slice (массив)](../../javascript/reference/slice-method-array-javascript.md)