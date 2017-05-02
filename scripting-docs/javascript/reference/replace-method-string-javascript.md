---
title: "Метод replace (String) (JavaScript) | Microsoft Docs"
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
  - "replace"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Replace - метод"
  - "замена строк"
ms.assetid: 5f0e4765-df4d-4887-bd09-efe5e58251bf
caps.latest.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 28
---
# Метод replace (String) (JavaScript)
Заменяет текст в строке, используя регулярное выражение или строку поиска.  
  
## Синтаксис  
  
```  
  
stringObj. replace(rgExp, replaceText)  
```  
  
## Параметры  
 `stringObj`  
 Обязательный.  Объект `String` или строковый литерал, в которых нужно выполнить замену.  Метод **replace** не меняет эту строку,  но значение, возвращаемое этим методом, представляет собой строку, созданную в результате замены.  
  
 `rgExp`  
 Обязательный.  Экземпляр объекта **Regular Expression**, содержащий шаблон регулярного выражения и установленные флаги.  Также может быть объектом `String` или строковым литералом, представляющим регулярное выражение.  Если `rgExp` не является экземпляром объекта **Regular Expression**, он преобразуется в строку, после чего выполняется поиск точного соответствия; попытки преобразовать строку в регулярное выражение не предпринимаются.  
  
 `replaceText`  
 Обязательный.  Объект `String` или строковый литерал, содержащий текст, на который необходимо заменить все найденные соответствия `rgExp` в `stringObj`.  В [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] и более поздних версиях аргумент `replaceText` может быть также функцией, возвращающей текст замены.  
  
## Возвращаемое значение  
 Результат применения метода **replace** представляет собой копию `stringObj` после внесения указанных замен.  
  
## Заметки  
 Все описанные ниже переменные соответствия можно использовать для определения последнего найденного соответствия и строки, из которой оно поступило.  Переменные соответствия можно использовать при замене текста в случае, если строка замены определяется динамически.  
  
|Знаки|Значение|  
|-----------|--------------|  
|**$$**|`$` \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] или более поздней версии\)|  
|**$&**|Определяет часть `stringObj`, которая полностью совпадает с шаблоном.  \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] или более поздней версии\)|  
|`$``|Определяет часть `stringObj`, которая предшествует совпадению, описанному параметром **$&**.  \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] или более поздней версии\)|  
|`$'`|Определяет часть `stringObj`, которая следует за совпадением, описанным параметром **$&**.  \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] или более поздней версии\)|  
|`$`  ***n***|Найденное частичное совпадение под номером *n*, где *n* — это одна десятичная цифра от 1 до 9.  \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] или более поздней версии\)|  
|`$`  ***nn***|Найденное частичное совпадение под номером *nn*, где *nn* — это одна десятичная цифра от 01 до 99.  \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] или более поздней версии\)|  
  
 Если `replaceText` является функцией, она вызывается для каждой найденной подстроки с описанными ниже аргументами *m* \+ 3, где *m* — число открывающих круглых скобок в `rgExp`.  Первым аргументом является найденная подстрока.  Следующие *m* аргументов — это все совпадения, обнаруженные в результате поиска.  Аргумент *m* \+ 2 — это смещение в пределах объекта `stringObj`, в котором нашлось совпадение, а аргумент *m* \+ 3 — это объект `stringObj`.  Результатом является строковое значение, полученное в результате замены каждой найденной подстроки на соответствующее возвращенное значение вызова функции.  
  
 Метод **replace** обновляет свойства глобального объекта `RegExp`.  
  
## Пример  
 В следующем примере показано использование метода **replace** для замены всех встречающихся в тесте артиклей the на артикль a.  
  
```javascript  
var s = "the batter hit the ball with the bat";  
  
// Replace "the" with "a".  
var re = /the/g;  
var result = s.replace(re, "a");  
document.write(result);  
// Output: a batter hit a ball with a bat  
```  
  
 Кроме того, метод **replace** позволяет заменять части выражений в шаблоне.  В следующем примере меняются местами все пары слов в строке.  
  
```javascript  
  
var s = "The quick brown fox jumped over the lazy dog.";  
var re = /(\S+)(\s+)(\S+)/g;  
// Exchange each pair of words.  
var result = s.replace(re, "$3$2$1");  
document.write(result);  
  
// Output:  quick The fox brown over jumps lazy the dog.  
```  
  
 В следующем примере, который работает в [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] и более поздних версиях, показано, как использовать функцию, возвращающую текст замены.  Она заменяет каждое число, после которого стоит буква F, на эквивалентное значение в градусах Цельсия.  
  
```javascript  
function f2c(s1) {  
    // Initialize pattern.  
    var test = /(\d+(\.\d*)?)F\b/g;  
  
    // Use a function for the replacement.  
    var s2 = s1.replace(test,  
      function($0,$1,$2)  
           {   
           return((($1-32) * 5/9) + "C");  
           }  
        )  
    return s2;  
}  
document.write(f2c("Water freezes at 32F and boils at 212F."));  
  
// Output: Water freezes at 0C and boils at 100C.  
  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Применение**: [Объект String](../../javascript/reference/string-object-javascript.md)  
  
## См. также  
 [Метод exec \(Regular Expression\)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [Метод match \(String\)](../../javascript/reference/match-method-string-javascript.md)   
 [Объект RegExp](../../javascript/reference/regexp-object-javascript.md)   
 [Метод search \(String\)](../../javascript/reference/search-method-string-javascript.md)   
 [Метод test \(Regular Expression\)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Regular Expression Programming \(JavaScript\)](http://msdn.microsoft.com/ru-ru/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [Alternation and Subexpressions \(JavaScript\)](http://msdn.microsoft.com/ru-ru/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [Backreferences \(JavaScript\)](http://msdn.microsoft.com/ru-ru/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)   
 [Пример приложения с перетаскиванием на HTML5](http://code.msdn.microsoft.com/Drag-and-drop-e2701a72)