---
title: "Объект регулярного выражения (JavaScript) | Microsoft Docs"
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
  - "RegularExpression_JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "RegExp - объект, общие сведения"
  - "Объект регулярного выражения"
  - "регулярные выражения, RegExp - объект"
ms.assetid: 346aa83e-a045-47ea-acae-b42c7b121534
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# Объект регулярного выражения (JavaScript)
Объект, который содержит шаблон регулярного выражения с флагами, определяющими, как применять шаблон.  
  
## Синтаксис  
  
```  
re = /pattern/[flags]  
```  
  
## Синтаксис  
  
```  
re = new RegExp("pattern"[,"flags"])   
```  
  
## Параметры  
 *re*  
 Обязательный.  Имя переменной, которой назначается шаблон регулярного выражения.  
  
 *pattern*  
 Обязательный.  Используемый шаблон регулярного выражения.  Если вы используете синтаксис 1, разделите шаблон с помощью символов «\/».  Если вы используете синтаксис 2, заключите шаблон в кавычки.  
  
 `flags`  
 Необязательно.  При использовании синтаксиса 2 заключите флаг в кавычки.  Доступные флаги, которые можно совместить:  
  
-   g \(глобальный поиск всех вхождений *шаблона*\);  
  
-   i \(не учитывать регистр\);  
  
-   m \(многостроковый поиск\);  
  
-   u \(Юникод\), включает [функции Юникода](../../javascript/advanced/special-characters-javascript.md) EcmaScript 6.  Поддерживается только в [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)];  
  
-   y \(прикрепленное совпадение\), ищет совпадения в свойстве `lastIndex` регулярного выражения \(и не ищет в более поздних индексах\).  Поддерживается в [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)].  
  
## Заметки  
 Объект **Regular Expression** не следует путать с глобальным объектом `RegExp`.  Несмотря на их кажущееся сходство, они отличаются.  Свойства объекта **Regular Expression** содержат только сведения о конкретном экземпляре **Regular Expression**, тогда как свойства глобального объекта `RegExp` содержат постоянно обновляющуюся информацию о каждом возникающем совпадении.  
  
 Объекты **Regular Expression** хранят шаблоны, используемые при поиске сочетаний символов в строках.  После создания объекта **Regular Expression** он передается в строковый метод или строка передается в один из методов регулярных выражений.  Сведения о последнем выполненном поиске хранятся в глобальном объекте `RegExp`.  
  
 Используйте синтаксис 1, если искомая строка заранее известна.  Используйте синтаксис 2, если искомая строка часто меняется или неизвестна \(примером может служить строка, взятая из входных данных от пользователя\).  
  
 Аргумент *pattern* компилируется во внутренний формат перед использованием.  В синтаксисе 1 аргумент *pattern* компилируется в ходе загрузки скрипта.  В синтаксисе 2 аргумент *pattern* компилируется перед использованием или при вызове метода **compile**.  
  
## Пример  
 В следующем примере показано использование объекта **Regular Expression** путем создания объекта \(re\), содержащего шаблон регулярного выражения со связанными флагами.  В этом случае полученный объект **Regular Expression** затем используется методом `match`:  
  
```javascript  
var s = "through the pages of the book";  
  
// Create regular expression pattern.  
var re = new RegExp("the", "i");  
  
// Attempt match on search string.  
var r = s.match(re);     
  
// Return first occurrence of "the".  
if(console && console.log) {  
    console.log(r);  
}  
  
// Output:  
//   
```  
  
## Пример  
 В следующем примере обновляется шаблон регулярного выражения: разрешается поиск нескольких экземпляров.  
  
```javascript  
// Create regular expression pattern using the i and g flags.  
var re = new RegExp("the", "ig");  
  
// Attempt match on search string.  
var r = s.match(re);     
  
// Return the two occurrences of "the".  
if(console && console.log) {  
    console.log(r.length);  
    console.log(r);  
}  
  
// Output:  
// 2  
// [object Array] ["the", "the"]  
```  
  
## Пример  
 Если используется флаг \/y, при нахождении совпадения он обновляет `lastindex` до индекса следующего символа после последнего совпадения.  При ненахождении совпадения он сбрасывает `lastindex` до 0.  
  
 В следующем примере выполняется поиск совпадения в определенном индексе с использованием флага \/y и свойства `lastIndex`.  
  
```javascript  
// Create regular expression pattern using the i and y flags.  
var re = new RegExp("the", "iy");  
  
// Set the lastIndex property and attempt a match  
// at the specified index.  
re.lastIndex = 20;  
var r = s.match(re);     
  
// No matches returned.  
if(console && console.log) {  
    console.log(r);  
}  
// Reset the lastIndex property and attempt a match.  
re.lastIndex = 21;  
var r = s.match(re);  
  
// Return occurrence of "the" starting at index 21.  
if(console && console.log) {  
    console.log(r);  
}  
  
// Output:  
// null  
// [object Array] ["the"]  
```  
  
<a name="js56jsobjregexpressionprop"></a>   
## Свойства  
 [Свойство global](../../javascript/reference/global-property-regular-expression-javascript.md) &#124; [Свойство ignoreCase](../../javascript/reference/ignorecase-property-regular-expression-javascript.md) &#124; [Свойство multiline](../../javascript/reference/multiline-property-regular-expression-javascript.md) &#124; [Свойство source](../../javascript/reference/source-property-regular-expression-javascript.md)  
  
<a name="js56jsobjregexpressionmeth"></a>   
## Методы  
 [Метод compile](../../javascript/reference/compile-method-regular-expression-javascript.md) &#124; [Метод exec](../../javascript/reference/exec-method-regular-expression-javascript.md) &#124; [Метод test](../../javascript/reference/test-method-regular-expression-javascript.md)  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 Флаг u поддерживается в [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)].  
  
 Флаг y поддерживается в [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)].  
  
## См. также  
 [Объект RegExp](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ru-ru/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Объект String](../../javascript/reference/string-object-javascript.md)