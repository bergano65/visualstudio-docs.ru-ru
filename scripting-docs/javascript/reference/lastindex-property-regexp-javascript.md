---
title: "Свойство lastIndex (RegExp) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "lastIndex"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "lastIndex - свойство"
ms.assetid: c8ae2a13-6dff-4cbe-b662-aca3d66c2a7f
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Свойство lastIndex (RegExp) (JavaScript)
Возвращает позицию знака, с которого начинается следующее найденное совпадение в строке для поиска.  
  
## Синтаксис  
  
```  
  
RegExp.lastIndex  
```  
  
## Заметки  
 Объект, связанный с этим свойством, — всегда глобальный объект `RegExp`.  
  
 Значения свойства `lastIndex` начинаются с нуля, это означает, что индекс первого знака равен нулю.  Начальным значением свойства является –1.  Это значение изменяется при каждом успешном обнаружении искомого выражения.  
  
 Свойство `lastIndex` изменяется методами `exec` и **test** объекта `RegExp` и методами `match`, **replace** и **split** объекта `String`.  
  
 К значениям свойства `lastIndex` применяются следующие правила.  
  
-   Если совпадения не найдены, то для свойства `lastIndex` устанавливается значение \-1.  
  
-   Если значение свойства `lastIndex` больше длины строки, то происходит сбой методов **test** и `exec`, а для свойства `lastIndex` устанавливается значение \-1.  
  
-   Если значение свойства `lastIndex` равно длине строки, то регулярное выражение совпадает при совпадении шаблона с пустой строкой.  В противном случае поиск завершается неудачей и свойство `lastIndex` сбрасывается к значению \-1.  
  
-   Во всех других случаях для свойства `lastIndex` устанавливается позиция, следующая за последним найденным совпадением.  
  
## Пример  
 В следующем примере показано использование свойства `lastIndex`.  Данная функция выполняет итерацию строки для поиска и печатает значения **index** и `lastIndex` для каждого слова в строке.  
  
```javascript  
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
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применение**: [Объект RegExp](../../javascript/reference/regexp-object-javascript.md)  
  
## См. также  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ru-ru/ab0766e1-7037-45ed-aa23-706f58358c0e)