---
title: "Свойство Index (RegExp) (JavaScript) | Документы Microsoft"
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
- index
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Index property
- matching strings
ms.assetid: d8be1ef6-1bf2-43cd-b0b5-567a61eabaad
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c6b11a5caf6e727b4d525b9a2d51eddd4542bc4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="index-property-regexp-javascript"></a>Свойство index (RegExp) (JavaScript)
Возвращает позицию символа, где начинается первого совпадения в строке для поиска. Только для чтения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RegExp.index   
```  
  
## <a name="remarks"></a>Примечания  
 Объект, связанный с этим свойством, всегда является глобальный `RegExp` объекта.  
  
 **Индекс** свойства начинается с нуля. Начальное значение **индекс** свойство имеет значение -1. Его значение изменяется при каждом обнаружении совпадения.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование **индекс** свойство. Эта функция выполняет итерацию искомую строку и выводит **индекс** и `lastIndex` значения для каждого слова в строке.  
  
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
      document.write (arr.index + "-" + arr.lastIndex + " ");  
      document.write (arr);  
      }  
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применяется к**: [объект RegExp](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Синтаксис регулярного выражения (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)