---
title: "Свойство lastMatch ($&amp;) (RegExp) (JavaScript) | Документы Microsoft"
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
- $&
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- lastMatch property ($%)
- lastMatch property ($&)
ms.assetid: d223836d-5235-48a5-a926-d20764ad3f14
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25991bf5b577d785fc4f7d8c6b2af14b93486000
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="lastmatch-property-amp-regexp-javascript"></a>Свойство lastMatch ($&amp;) (RegExp) (JavaScript)
Возвращает последние символы сопоставленная поиске регулярного выражения. Только для чтения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RegExp.lastMatch  
```  
  
## <a name="remarks"></a>Примечания  
 Объект, связанный с этим свойством, всегда является глобальный `RegExp` объекта.  
  
 Начальное значение `lastMatch` свойства является пустая строка. Значение `lastMatch` свойство изменяется при каждом обнаружении совпадения.  
  
## <a name="example"></a>Пример  
 В следующем примере показано применение свойства `lastMatch`.  
  
```JavaScript  
// Create the regular expression pattern.  
var re = new RegExp("d(b+)(d)","ig");  
var str = "cdbBdbsbdbdz";  
  
// Perform the search.  
var arr = re.exec(str);  
  
// Print the output.  
var s = ""   
s += "$1: " + RegExp.$1 + "<br />";  
s += "$2: " + RegExp.$2 + "<br />";  
s += "$3: " + RegExp.$3 + "<br />";  
s += "input: " + RegExp.input + "<br />";  
s += "lastMatch: " + RegExp.lastMatch + "<br />";  
s += "leftContext: " + RegExp.leftContext + "<br />";  
s += "rightContext: " + RegExp.rightContext + "<br />";   
s += "lastParen: " + RegExp.lastParen + "<br />";  
  
document.write(s);  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Применяется к**: [объект RegExp](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [$1... $9 свойства (RegExp)](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md)   
 [Свойство Index (RegExp)](../../javascript/reference/index-property-regexp-javascript.md)   
 [Свойство Input ($_) (RegExp)](../../javascript/reference/input-property-dollar-regexp-javascript.md)   
 [Свойство lastIndex (RegExp)](../../javascript/reference/lastindex-property-regexp-javascript.md)   
 [Свойство lastParen ($ +) (RegExp)](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md)   
 [Свойство leftContext ($') (RegExp)](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md)   
 [Свойство rightContext ($') (RegExp)](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)