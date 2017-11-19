---
title: "Метод Split (String) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: split
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: split method
ms.assetid: 7f093336-c887-4efb-b91f-819b6d18a181
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eea90dda2e8e4d52451af247d139eeee44f83917
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="split-method-string-javascript"></a>Метод split (String) (JavaScript)
Разбивает строку на подстроки, используя заданный разделитель, и возвращает их в виде массива.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
stringObj.split([separator[, limit]])  
```  
  
## <a name="parameters"></a>Параметры  
 `stringObj`  
 Обязательный. Объект `String` или строковый литерал, который необходимо разделить. Этот объект не был изменен **разбиение** метод.  
  
 `separator`  
 Необязательно. Строка или объект **регулярное выражение** , определяющий символ или символы, используемые при разделении строк. Если этот параметр не указан, возвращается одноэлементный массив, содержащий всю строку.  
  
 `limit`  
 Необязательно. Значение, ограничивающее число элементов, возвращаемых в массиве.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Результат **разбиение** метод представляет собой массив строк, разделенных в каждой точке, где `separator` происходит в `stringObj`. Аргумент `separator` не возвращается как часть какого-либо элемента массива.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование **разбиение** метод.  
  
```JavaScript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.split(" ");  
for (var i in ss) {  
    document.write(ss[i]);  
    document.write("<br/>");  
}  
  
// Output:   
// The  
// quick  
// brown  
// fox  
// jumps  
// over  
// the  
// lazy  
// dog.  
  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применяется к**: [строковый объект](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод concat (строка)](../../javascript/reference/concat-method-string-javascript.md)   
 [Объект RegExp](../../javascript/reference/regexp-object-javascript.md)   
 [Объект регулярного выражения](../../javascript/reference/regular-expression-object-javascript.md)   
 [Синтаксис регулярного выражения (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Прокрутки, сдвига и масштабирования примера приложения](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)