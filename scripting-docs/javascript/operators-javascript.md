---
title: "Операторы (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JavaScript, операторы"
ms.assetid: b8602b69-aba9-46e8-86e1-cb533ad41410
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Операторы (JavaScript)
В [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] содержится целый ряд операторов, которые можно разделить на арифметические, логические, побитовые операторы, операторы присваивания и разнообразное множество других операторов.  Для объяснений и примеров см. разделы, посвященные определенным операторам.  
  
## Операторы вычислений  
  
|Описание|Символ|  
|--------------|------------|  
|[Унарное отрицание](../javascript/reference/subtraction-operator-decrement-javascript.md)|\-|  
|[Инкремент](../javascript/reference/increment-and-decrement-operators-javascript.md)|\+\+|  
|[Декремент](../javascript/reference/increment-and-decrement-operators-javascript.md)|\-\-|  
|[Умножение](../javascript/reference/multiplication-operator-decrement-javascript.md)|\*|  
|[Деление](../javascript/reference/division-operator-decrement-javascript.md)|\/|  
|[Арифметический модуль](../javascript/reference/modulus-operator-decrementjavascript.md)|%|  
|[Сложение](../javascript/reference/addition-operator-decrement-javascript.md)|\+|  
|[Вычитание](../javascript/reference/subtraction-operator-decrement-javascript.md)|\-|  
  
## Логические операторы  
  
|Описание|Символ|  
|--------------|------------|  
|[Логическое НЕ](../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)|\!|  
|[Меньше](../javascript/reference/comparison-operators-javascript.md)|\<|  
|[Больше](../javascript/reference/comparison-operators-javascript.md)|\>|  
|[Меньше или равно](../javascript/reference/comparison-operators-javascript.md)|\<\=|  
|[Больше или равно](../javascript/reference/comparison-operators-javascript.md)|\>\=|  
|[Равенство](../javascript/reference/comparison-operators-javascript.md)|\=\=|  
|[Неравенство](../javascript/reference/comparison-operators-javascript.md)|\!\=|  
|[Логическое И](../javascript/reference/logical-and-operator-decrement-javascript.md)|&&|  
|[Логическое ИЛИ](../javascript/reference/logical-or-operator-decrement-javascript.md)|&#124;&#124;|  
|[Условный \(троичный\)](../javascript/reference/conditional-ternary-operator-decrement-javascript.md)|?:|  
|[Запятая](../javascript/reference/comma-operator-decrement-javascript.md)|,|  
|[Строгое равенство](../javascript/reference/comparison-operators-javascript.md)|\=\=\=|  
|[Строгое неравенство](../javascript/reference/comparison-operators-javascript.md)|\!\=\=|  
  
## Побитовые операторы  
  
|Описание|Символ|  
|--------------|------------|  
|[Побитовое НЕ](../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)|~|  
|[Побитовый сдвиг влево](../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)|\<\<|  
|[Побитовый сдвиг вправо](../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)|\>\>|  
|[Сдвиг вправо без учета знака](../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)|\>\>\>|  
|[Побитовое И](../javascript/reference/bitwise-and-operator-decrement-javascript.md)|&|  
|[Побитовое исключающее ИЛИ](../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)|^|  
|[Побитовое ИЛИ](../javascript/reference/bitwise-or-operator-decrement-javascript.md)|&#124;|  
  
## Операторы присваивания  
  
|Описание|Символ|  
|--------------|------------|  
|[Присваивание](../javascript/reference/assignment-operator-decrement-equal-javascript.md)|\=|  
|[Составное присваивание](../javascript/reference/compound-assignment-operators-javascript.md)|*OP*\= \(например \+\= и &\=\)|  
  
## Прочие операторы  
  
|Описание|Символ|  
|--------------|------------|  
|[delete](../javascript/reference/delete-operator-decrementjavascript.md)|delete|  
|[typeof](../javascript/reference/typeof-operator-decrementjavascript.md)|typeof|  
|[void](../javascript/reference/void-operator-decrementjavascript.md)|void|  
|[instanceof](../javascript/reference/instanceof-operator-decrementjavascript.md)|instanceof|  
|[new;](../javascript/reference/new-operator-decrementjavascript.md)|new;|  
|[in](../javascript/reference/in-operator-decrementjavascript.md)|in|  
  
## Равенство и строгое равенство  
 Различие между \=\= \(равенством\) и \=\=\= \(строгим равенством\) заключается в том, что оператор равенства перед проверкой на равенство приведет значения различных типов к одному типу.  Например, сравнение строки "1" с числом 1 возвратит true.  При этом оператор строгого равенства не приводит значения различных типов к одному типу, поэтому строка "1" не будет равна 1 при сравнении.  
  
 Простые строки, числа и логические значения сравниваются по значению.  Если они имеют одинаковое значение, они равны.  Объекты \(включая объекты `Array`, `Function`, `String`, **Number**, `Boolean`, **Error**, `Date` и `RegExp`\) сравниваются по ссылке.  Даже если две переменные этих типов имеют одинаковое значение, они равны только в том случае, если они ссылаются на один и тот же объект.  
  
 Например:  
  
```javascript  
// Two strings with the same value.  
var string1 = "Hello";  
var string2 = "Hello";  
  
// Two String objects with the same value.  
var StringObject1 = new String(string1);  
var StringObject2 = new String(string2);  
  
if (string1 == string2)  
    document.write("string1 is equal to string2 <br/>");  
  
if (StringObject1 != StringObject2)  
    document.write("StringObject1 is not equal to StringObject2 <br/>");  
  
// To compare the values of String objects, use the toString() or valueOf() methods.  
if (StringObject1.valueOf() == StringObject2.valueOf())  
    document.write("The value of StringObject1 is equal to the value of StringObject2");  
  
//Output:  
// string1 is equal to string2   
// StringObject1 is not equal to StringObject2   
// The value of StringObject1 is equal to the value of StringObject2  
  
```