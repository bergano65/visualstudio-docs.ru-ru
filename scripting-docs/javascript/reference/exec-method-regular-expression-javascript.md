---
title: "Метод exec (Regular Expression) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: exec
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- matching strings
- Exec method
ms.assetid: 83092452-60cc-4218-b4ae-af9e3cb96c34
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 426cc1a8162b03090289cf737a03d64a75df77e9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="exec-method-regular-expression-javascript"></a>Метод exec (Regular Expression) (JavaScript)
Выполняет поиск строки с помощью шаблона регулярного выражения и возвращает массив, содержащий результаты поиска.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
rgExp.exec(str)   
```  
  
## <a name="parameters"></a>Параметры  
 `rgExp`  
 Обязательный. Экземпляр **регулярное выражение** объект, содержащий шаблон регулярного выражения и установленные флаги.  
  
 `str`  
 Обязательный. `String` Или строковый литерал, в котором выполняется поиск.  
  
## <a name="remarks"></a>Примечания  
 Если `exec` метод не найден, возвращается значение `null`. При обнаружении совпадения, `exec` возвращает массив, а свойства глобального `RegExp` объекта будут обновлены в соответствии с результатами совпадения. Нулевой элемент массива содержит полное совпадение, элементы с 1 -  *n*  содержат только вложенные совпадения, которые произошли в соответствие. Такое поведение идентично поведение `match` метод без глобального флага (**g**) значение.  
  
 Если глобальный флаг установлен для регулярного выражения, `exec` выполняет поиск строк, начиная с позиции, указываемой параметром значение `lastIndex`. Если глобальный флаг не установлен, `exec` игнорирует значение `lastIndex` и выполняет поиск с начала строки.  
  
 Массив, возвращаемый методом `exec` метод имеет три свойства **ввода**, **индекс** и **lastIndex.** **Ввода** свойство содержит весь искомая строка. **Индекс** свойство содержит позицию сопоставленной подстроки в пределах завершения искомая строка. `lastIndex` Свойство содержит положение после последнего символа в соответствие.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование `exec` метода:  
  
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
      document.write (arr[0]);  
      }  
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применяется к**: [объект регулярного выражения](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод Match (String)](../../javascript/reference/match-method-string-javascript.md)   
 [Объект RegExp](../../javascript/reference/regexp-object-javascript.md)   
 [Синтаксис регулярного выражения (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Метод Search (String)](../../javascript/reference/search-method-string-javascript.md)   
 [Метод Test (Regular Expression)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Программирование регулярных выражений (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)