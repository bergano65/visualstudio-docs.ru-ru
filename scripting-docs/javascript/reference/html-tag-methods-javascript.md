---
title: "Методы HTML-тегов (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "anchor - метод [JavaScript]"
  - "big - метод [JavaScript]"
  - "blink - метод [JavaScript]"
  - "bold - метод [JavaScript]"
  - "fixed - метод [JavaScript]"
  - "fontcolor - метод [JavaScript]"
  - "fontsize -метод [JavaScript]"
  - "методы HTML-тегов [JavaScript]"
  - "italics - метод [JavaScript]"
  - "link - метод [JavaScript]"
  - "small - метод [JavaScript]"
  - "sub -метод [JavaScript]"
  - "sup - метод [JavaScript]"
ms.assetid: 50376223-be95-4aa4-9147-9e738a5d3cfa
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Методы HTML-тегов (JavaScript)
Можно использовать методы HTML\-тегов для размещения элементов HTML вокруг текста в объекте `String`.  
  
## Синтаксис  
 В следующей таблице описан синтаксис для каждого метода HTML\-тега и дано его описание.  
  
 В столбце "Синтаксис" `string1` — это объект `String` или литерал.  
  
 Столбец "Стандарт" указывает рекомендации [консорциума W3C](http://go.microsoft.com/fwlink/?LinkId=199553) для HTML 4.  "Не рекомендуется" означает, что вместо HTML\-элемента лучше использовать таблицы стилей.  
  
|Синтаксис|Описание метода|Описание параметра|Стандарт|  
|---------------|---------------------|------------------------|--------------|  
|`string1`.anchor\(`name`\)|Заключает текст в привязку HTML, имеющую атрибут NAME.|Параметр `name` — это текст, который помещается в атрибут NAME привязки HTML.||  
|`string1`.big \(\)|Заключает текст в HTML\-теги \<BIG\>.||Не рекомендуется|  
|`string1`.blink \(\)|Заключает текст в HTML\-теги \<BLINK\>.  Теги \<BLINK\> не поддерживаются в Internet Explorer.||Нет в стандарте|  
|`string1`.bold\(\)|Заключает текст в HTML\-теги \<B\>.||Не рекомендуется|  
|`string1`.fixed\(\)|Заключает текст в HTML\-теги \<TT\>.||Не рекомендуется|  
|`string1`.fontcolor\(`color`\)|Заключает текст в HTML\-теги \<FONT\> с атрибутом COLOR.|Параметр `color` — это строковое значение, содержащее шестнадцатеричное значение или стандартное имя цвета.  Допустимые стандартные имена цветов зависят от браузера, где используется [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], и его версии.|Устарело|  
|`string1`.fontsize\(`size`\)|Заключает текст в HTML\-теги \<FONT\> с атрибутом SIZE.|Параметр `size` — целое число, задающее размер текста.  Допустимые целые числа зависят от браузера, где используется [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], и его версии.|Устарело|  
|`string1`.italics\(\)|Заключает текст в HTML\-теги \<I\>.||Не рекомендуется|  
|`string1`.link\(`href`\)|Заключает текст в привязку HTML, имеющую атрибут HREF.|Параметр `href` — это текст, который помещается в атрибут HREF привязки HTML.||  
|`string1`.small\(\)|Заключает текст в HTML\-теги \<SMALL\>.||Не рекомендуется|  
|`string1`.strike\(\)|Заключает текст в HTML\-теги \<STRIKE\>.||Устарело|  
|`string1`.sub\(\)|Заключает текст в HTML\-теги \<SUB\>.|||  
|`string1`.sup\(\)|Заключает текст в HTML\-теги \<SUP\>.|||  
  
## Заметки  
 Проверка того, применены ли уже HTML\-теги к строке не выполняется.  
  
## Пример  
 В следующих примерах показано использование методов HTML\-тегов.  
  
```javascript  
// anchor method.  
var strVariable = "This is an anchor.";  
document.write(strVariable.anchor("Anchor1"));  
// Output: <A NAME="Anchor1">This is an anchor.</A>  
  
// big method.  
var strVariable = "This is a string.";  
document.write(strVariable.big());  
// Output: <BIG>This is a string.</BIG>  
  
//  blink method.  
var strVariable = "This is a string.";  
document.write(strVariable.blink());  
// Output: <BLINK>This is a string.</BLINK>  
  
//  bold method.  
var strVariable = "This is a string.";  
document.write(strVariable.bold());  
// Output: <B>This is a string.</B>  
  
//  fixed method.  
var strVariable = "This is a string.";  
document.write(strVariable.fixed());  
// Output: <TT>This is a string.</TT>  
  
//  fontcolor method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontcolor("red"));  
// Output: <FONT COLOR="red">This is a string.</FONT>  
  
//  fontsize method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontsize(-1));  
// Output: <FONT SIZE="-1">This is a string.</FONT>  
  
//  italics method  
var strVariable = "This is a string.";  
document.write(strVariable.italics());  
// Output: <I>This is a string.</I>  
  
//  link method.  
var strVariable = "This is a hyperlink.";  
document.write(strVariable.link("http://www.microsoft.com"));  
// Output: <A HREF="http://www.microsoft.com">This is a hyperlink.</A>  
  
//  small method.  
var strVariable = "This is a string.";  
document.write(strVariable.small());  
// Output: <SMALL>This is a string.</SMALL>  
  
//  strike method.  
var strVariable = "This is a string.";  
document.write(strVariable.strike());  
// Output: <STRIKE>This is a string.</STRIKE>  
  
//  sub method.  
var strVariable = "This is a string.";  
document.write(strVariable.sub());  
// Output: <SUB>This is a string.</SUB>  
  
//  sup method.  
var strVariable = "This is a string.";  
document.write(strVariable.sup());  
// Output: <SUP>This is a string.</SUP>  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Относится к**: [Объект String](../../javascript/reference/string-object-javascript.md)  
  
## См. также  
 [Объект String](../../javascript/reference/string-object-javascript.md)