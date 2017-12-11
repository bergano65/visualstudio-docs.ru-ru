---
title: "Операторы (JavaScript) | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: JavaScript, operators
ms.assetid: b8602b69-aba9-46e8-86e1-cb533ad41410
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9d0a098418399dba19b77a12c057a3fba334e31
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="operators-javascript"></a>Операторы (JavaScript)
В [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] имеется полный набор операторов, включая арифметические, логические, битовые операторы, операторы присваивания, а также ряд операторов другого назначения. Их описание и примеры см. в соответствующих разделах.  
  
## <a name="computational-operators"></a>Операторы вычислений  
  
|Описание|Символ|  
|-----------------|------------|  
|[Унарное отрицание](../javascript/reference/subtraction-operator-decrement-javascript.md)|-|  
|[Инкремент](../javascript/reference/increment-and-decrement-operators-javascript.md)|++|  
|[Декремент](../javascript/reference/increment-and-decrement-operators-javascript.md)|--|  
|[Умножение](../javascript/reference/multiplication-operator-decrement-javascript.md)|*|  
|[Деление](../javascript/reference/division-operator-decrement-javascript.md)|/|  
|[Арифметический модуль](../javascript/reference/modulus-operator-decrementjavascript.md)|%|  
|[Сложение](../javascript/reference/addition-operator-decrement-javascript.md)|+|  
|[Вычитание](../javascript/reference/subtraction-operator-decrement-javascript.md)|-|  
  
## <a name="logical-operators"></a>Логические операторы  
  
|Описание|Символ|  
|-----------------|------------|  
|[Логическое НЕ](../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)|!|  
|[Меньше](../javascript/reference/comparison-operators-javascript.md)|\<|  
|[Больше](../javascript/reference/comparison-operators-javascript.md)|>|  
|[Меньше или равно](../javascript/reference/comparison-operators-javascript.md)|\<=|  
|[Больше или равно](../javascript/reference/comparison-operators-javascript.md)|>=|  
|[Равенство](../javascript/reference/comparison-operators-javascript.md)|==|  
|[Неравенство](../javascript/reference/comparison-operators-javascript.md)|!=|  
|[Логическое И](../javascript/reference/logical-and-operator-decrement-javascript.md)|&&|  
|[Логическое ИЛИ](../javascript/reference/logical-or-operator-decrement-javascript.md)|&#124;&#124;|  
|[Условный (троичный)](../javascript/reference/conditional-ternary-operator-decrement-javascript.md)|?:|  
|[Запятая](../javascript/reference/comma-operator-decrement-javascript.md)|,|  
|[Строгое равенство](../javascript/reference/comparison-operators-javascript.md)|===|  
|[Строгое неравенство](../javascript/reference/comparison-operators-javascript.md)|!==|  
  
## <a name="bitwise-operators"></a>Побитовые операторы  
  
|Описание|Символ|  
|-----------------|------------|  
|[Побитовое НЕ](../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)|~|  
|[Побитовый сдвиг влево](../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)|<\<|  
|[Побитовый сдвиг вправо](../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)|>>|  
|[Сдвиг вправо без учета знака](../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)|>>>|  
|[Побитовое И](../javascript/reference/bitwise-and-operator-decrement-javascript.md)|&|  
|[Побитовое исключающее ИЛИ](../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)|^|  
|[Побитовое ИЛИ](../javascript/reference/bitwise-or-operator-decrement-javascript.md)|&#124;|  
  
## <a name="assignment-operators"></a>Операторы присваивания  
  
|Описание|Символ|  
|-----------------|------------|  
|[Назначение](../javascript/reference/assignment-operator-decrement-equal-javascript.md)|=|  
|[Составное присваивание](../javascript/reference/compound-assignment-operators-javascript.md)|*OP*= (например, += и &=)|  
  
## <a name="miscellaneous-operators"></a>Прочие операторы  
  
|Описание|Символ|  
|-----------------|------------|  
|[delete](../javascript/reference/delete-operator-decrementjavascript.md)|удалить|  
|[typeof](../javascript/reference/typeof-operator-decrementjavascript.md)|typeof|  
|[void](../javascript/reference/void-operator-decrementjavascript.md)|void|  
|[instanceof](../javascript/reference/instanceof-operator-decrementjavascript.md)|instanceof|  
|[new](../javascript/reference/new-operator-decrementjavascript.md)|new|  
|[in](../javascript/reference/in-operator-decrementjavascript.md)|в|  
  
## <a name="equality-and-strict-equality"></a>Равенство и строгое равенство  
 Различие между операторами == (равенство) и === (строгое равенство) в том, что первый из них приводит значения разных типов перед проверкой равенства. Например, результатом сравнения строки "1" с числом 1 будет значение true. Оператор строго равенства, в свою очередь, не приводит значения разных типов, поэтому строка "1" не будет равна числу 1.  
  
 Простые строки, числа и логические значения сравниваются по значению. Если их значения совпадают, они считаются равными. Объекты (включая `Array`, `Function`, `String`, **Number**, `Boolean`, **Error**, `Date` и `RegExp`) сравниваются по ссылке. Даже если две переменные этих типов имеют одинаковые значения, они равны, только если относятся к одному и тому же объекту.  
  
 Например:  
  
```JavaScript  
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