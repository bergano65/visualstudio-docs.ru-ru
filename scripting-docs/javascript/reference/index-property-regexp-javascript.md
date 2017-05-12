---
title: "Свойство index (RegExp) (JavaScript) | Microsoft Docs"
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
  - "index"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Index - свойство"
  - "совпадающие строки"
ms.assetid: d8be1ef6-1bf2-43cd-b0b5-567a61eabaad
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Свойство index (RegExp) (JavaScript)
Возвращает позицию знака, с которого начинается первое найденное совпадение в строке для поиска.  Только для чтения.  
  
## Синтаксис  
  
```  
  
RegExp.index   
```  
  
## Заметки  
 Объект, связанный с данным свойством, всегда является глобальным объектом `RegExp`.  
  
 Значения свойства **index** начинаются с нуля.  Начальным значением свойства **index** является \-1.  Его значение изменяется при каждом успешном обнаружении искомого выражения.  
  
## Пример  
 В следующем примере показано использование свойства **index**.  Данная функция выполняет итерацию строки для поиска и печатает значения **index** и `lastIndex` для каждого слова в строке.  
  
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
      document.write (arr.index + "-" + arr.lastIndex + " ");  
      document.write (arr);  
      }  
}  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Относится к**: [Объект RegExp](../../javascript/reference/regexp-object-javascript.md)  
  
## См. также  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ru-ru/ab0766e1-7037-45ed-aa23-706f58358c0e)