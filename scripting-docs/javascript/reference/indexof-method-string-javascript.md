---
title: "Метод indexOf (строка) (JavaScript) | Документы Microsoft"
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
- indexOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- indexOf method, string
- string, indexOf method
ms.assetid: a17372fa-669b-471b-9240-46927a265152
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ecd96acb21f9d7711f9ee00dbf1c1bb70705c0d8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="indexof-method-string-javascript"></a>Метод indexOf (строка) (JavaScript)
Возвращает позицию первого вхождения подстроки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
strObj. indexOf(subString[, startIndex])  
```  
  
## <a name="parameters"></a>Параметры  
 `strObj`  
 Обязательный. Объект `String` или строковый литерал.  
  
 `subString`  
 Обязательный. Подстрока, которую необходимо найти в строке  
  
 `startIndex`  
 Необязательно. Индекс, с которого необходимо начать поиск объекта `String`. Если он не указан, поиск будет производиться с начала строки.  
  
## <a name="remarks"></a>Примечания  
 **IndexOf** возвращает начало подстроки в `String` объекта. Если подстрока не найдена, возвращается -1.  
  
 Если значение `startindex` отрицательно, то `startindex` рассматривается как ноль. Если его значение больше наибольшего индекса, он рассматривается как наибольший индекс.  
  
 Поиск выполняется слева направо. В противном случае этот метод идентичен **lastIndexOf**.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование **indexOf** метод.  
  
```JavaScript  
var str = "original equipment manufacturer";  
  
var s = "equip is at position " + str.indexOf("equip");  
s += "<br />";  
s += "abc is at position " + str.indexOf("abc");  
  
document.write(s);  
  
// Output:  
// equip is at position 9  
// abc is at position -1  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применяется к**: [строковый объект](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод lastIndexOf (строка)](../../javascript/reference/lastindexof-method-string-javascript.md)   
 [Прокрутки, сдвига и масштабирования примера приложения](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)