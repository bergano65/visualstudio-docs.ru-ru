---
title: "Метод match (String) (JavaScript) | Microsoft Docs"
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
  - "match"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Match - метод"
ms.assetid: eda9ad27-4f9b-4cb1-8345-a0ae85979ca0
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# Метод match (String) (JavaScript)
Выполняет поиск по строке с использованием регулярного выражения и возвращает массив, содержащий результаты поиска.  
  
## Синтаксис  
  
```  
  
stringObj.match(rgExp)   
```  
  
## Параметры  
 `stringObj`  
 Обязательное.  Объект `String` или строковый литерал, по которому выполняется поиск.  
  
 `rgExp`  
 Обязательное.  Объект регулярного выражения, содержащий шаблон регулярного выражения и применимые флаги.  Это может также быть переменная или строковый литерал, содержащий шаблон регулярного выражения и флаги.  
  
## Заметки  
 Если метод `match` не находит совпадений, возвращается результат `null`.  Если совпадение найдено, метод `match` возвращает массив, а свойства глобального объекта `RegExp` обновляются в соответствии с результатами совпадения.  
  
 Если глобальный флаг \(`g`\) не установлен, нулевой элемент массива содержит совпадение целиком, в то время как элементы от 1 до *n* содержат все вложенные совпадения, найденные внутри совпадения.  Такое поведение идентично поведению метода [Метод exec \(Regular Expression\)](../../javascript/reference/exec-method-regular-expression-javascript.md) без установленного глобального флага.  Если глобальный флаг установлен, элементы от 0 до *n* содержат все найденные совпадения.  
  
 Если глобальный флажок не установлен, то массив, возвращаемый методом `match`, имеет 2 свойства: `input` и `index`.  Свойство `input` содержит всю строку, по которой выполнялся поиск.  Свойство `index` содержит положение совпавшей подстроки внутри целой строки, по которой выполнялся поиск.  
  
 Если флаг `i` установлен, то при поиске регистр не учитывается.  
  
## Пример  
 В следующем примере показано использование метода `match`.  
  
```javascript  
var src = "azcafAJAC";  
  
var re = /[a-c]/;  
  
var result = src.match(re);  
  
// The entire match is in array element 0.  
document.write(result[0] + "<br/>");  
  
// Now try the same match with the global flag.  
var reg = /[a-c]/g;  
result = src.match(reg);  
  
// The matches are in elements 0 through n.  
for (var index = 0; index < result.length; index++)  
{  
    document.write ("submatch " + index + ": " +  result[index]);  
    document.write("<br />");  
}  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применяется к**: [Объект String](../../javascript/reference/string-object-javascript.md)  
  
## См. также  
 [Метод exec \(Regular Expression\)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [Объект RegExp](../../javascript/reference/regexp-object-javascript.md)   
 [Объект Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Метод replace \(строка\)](../../javascript/reference/replace-method-string-javascript.md)   
 [Метод search \(String\)](../../javascript/reference/search-method-string-javascript.md)   
 [Метод test \(Regular Expression\)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Regular Expression Programming \(JavaScript\)](http://msdn.microsoft.com/ru-ru/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [Alternation and Subexpressions \(JavaScript\)](http://msdn.microsoft.com/ru-ru/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [Backreferences \(JavaScript\)](http://msdn.microsoft.com/ru-ru/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)