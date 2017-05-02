---
title: "Метод exec (Regular Expression) (JavaScript) | Microsoft Docs"
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
  - "exec"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Exec - метод"
  - "совпадающие строки"
ms.assetid: 83092452-60cc-4218-b4ae-af9e3cb96c34
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Метод exec (Regular Expression) (JavaScript)
Выполняет поиск по строке с помощью шаблона регулярного выражения и возвращает массив, содержащий результаты поиска.  
  
## Синтаксис  
  
```  
  
rgExp.exec(str)   
```  
  
## Параметры  
 `rgExp`  
 Обязательный.  Экземпляр объекта **Regular Expression**, содержащий шаблон регулярного выражения и применимые флаги.  
  
 `str`  
 Обязательный.  Объект `String` или строковый литерал, в котором выполняется поиск.  
  
## Заметки  
 Если метод `exec` не находит совпадений, возвращается результат `null`.  Если совпадение найдено, метод `exec` возвращает массив, а свойства глобального объекта `RegExp` обновляются в соответствии с результатами совпадения.  Нулевой элемент массива содержит полное совпадение, а элементы с 1 по *n* содержат подсовпадения, обнаруженные внутри совпадения.  Такое поведение совпадает с поведением метода `match` без установленного глобального флага \(**g**\).  
  
 Если для регулярного выражения установлен глобальный флаг, метод `exec` выполняет поиск в строке, начиная с позиции, указанной значением `lastIndex`.  Если глобальный флаг не установлен, метод `exec` игнорирует значение `lastIndex` и выполняет поиск с начала строки.  
  
 Массив, возвращенный методом `exec`, имеет три свойства: **input**, **index** и **lastIndex**. Свойство **input** содержит всю строку, по которой выполнялся поиск.  Свойство **index** содержит положение совпавшей подстроки внутри целой строки, по которой выполнялся поиск.  Свойство `lastIndex` содержит положение после последнего знака совпадения.  
  
## Пример  
 В следующем примере показано использование метода `exec`.  
  
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
      document.write (arr[0]);  
      }  
}  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Относится к**: [Объект Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)  
  
## См. также  
 [Метод match \(String\)](../../javascript/reference/match-method-string-javascript.md)   
 [Объект RegExp](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ru-ru/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Метод search \(String\)](../../javascript/reference/search-method-string-javascript.md)   
 [Метод test \(Regular Expression\)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Regular Expression Programming \(JavaScript\)](http://msdn.microsoft.com/ru-ru/3b62e27c-4f07-4726-a95b-6e841807bfaf)