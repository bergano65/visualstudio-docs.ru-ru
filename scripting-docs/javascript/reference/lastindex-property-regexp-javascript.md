---
title: Свойство lastIndex (RegExp) (JavaScript) | Документы Microsoft
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
- lastIndex
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- lastIndex property
ms.assetid: c8ae2a13-6dff-4cbe-b662-aca3d66c2a7f
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5e24fe14d335e1494b13518543f56025625de0b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637814"
---
# <a name="lastindex-property-regexp-javascript"></a>Свойство lastIndex (RegExp) (JavaScript)
Возвращает позицию символа, где начинается следующего совпадения в строке для поиска.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RegExp.lastIndex  
```  
  
## <a name="remarks"></a>Примечания  
 Объект, связанный с этим свойством, всегда является глобальный `RegExp` объекта.  
  
 `lastIndex` Свойства начинается с нуля, индекс первого символа является ноль. Исходное значение равно -1. Это значение изменяется при каждом обнаружении совпадения.  
  
 `lastIndex` Изменено свойство `exec` и **тестирования** методы `RegExp` объекта и `match`, **заменить**, и **разбиение**методы `String` объекта.  
  
 Следующие правила применяются к значениям `lastIndex`:  
  
-   Если нет соответствия `lastIndex` имеет значение -1.  
  
-   Если `lastIndex` больше, чем длина строки, **тестирования** и `exec` ошибкой и `lastIndex` имеет значение -1.  
  
-   Если `lastIndex` — равным длине строки совпадений регулярного выражения, если шаблон соответствует пустая строка. В противном случае соответствие считается неудачным и `lastIndex` сбрасывается в значение -1.  
  
-   В противном случае `lastIndex` устанавливается в следующую позицию после последнего найденного соответствия.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование `lastIndex` свойство. Эта функция выполняет итерацию искомую строку и выводит **индекс** и `lastIndex` значения для каждого слова в строке.  
  
```JavaScript  
function RegExpTest()  
{  
   var ver = Number(ScriptEngineMajorVersion() + "." + ScriptEngineMinorVersion())  
   if (ver < 5.5)  
   {  
      document.write("You need a newer version of JavaScript for this to work");  
      return;  
   }  
  
   var src = "The quick brown fox jumps over the lazy dog.";  
  
   // Create regular expression pattern with a global flag.  
   var re = /\w+/g;  
  
   // Get the next word, starting at the position of lastindex.  
   var arr;  
   while ((arr = re.exec(src)) != null)  
      {  
      // New line:  
      document.write ("<br />");    
      document.write (arr.index + "-" + re.lastIndex + " ");  
      document.write (arr);  
      }  
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применяется к**: [объект RegExp](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Синтаксис регулярного выражения (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)