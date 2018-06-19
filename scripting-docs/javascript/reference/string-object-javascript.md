---
title: Строковый объект (JavaScript) | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- String_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- String object
- String object, overview
ms.assetid: 8063ecd5-5778-4e87-b985-b21420171914
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d58f567bb301b29324fee8ed75fc95fd1a4791ea
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24642194"
---
# <a name="string-object-javascript"></a>Объект String (JavaScript)
Позволяет управлять текстовыми строками, форматировать их и выполнять поиск подстрок в строках.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
newString = new String(["stringLiteral"])  
```  
  
## <a name="parameters"></a>Параметры  
 `newString`  
 Обязательный. Имя переменной, которой присваивается объект `String`.  
  
 `stringLiteral`  
 Необязательно. Любая группа символов Юникода.  
  
## <a name="remarks"></a>Примечания  
 Для представления знаков, которые невозможно ввести без преобразования, в [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] предусмотрены escape-последовательности, включаемые в строки. Например, `\t` обозначает символ табуляции. См. дополнительные сведения о [специальных символах](../../javascript/advanced/special-characters-javascript.md).  
  
## <a name="string-literals"></a>Строковые литералы  
 Объект *строковый литерал* является ноль или более символов, заключенных в одинарные или двойные кавычки. Строковый литерал содержит основной (примитивный) тип данных `string`. Объект *строковый объект* создается с помощью [оператор new](../../javascript/reference/new-operator-decrementjavascript.md), и имеет тип данных `Object`.  
  
 В следующем примере показано, что тип данных строкового литерала отличается от типа данных объекта `String`.  
  
```JavaScript  
var strLit = "This is a string literal.";  
var strObj = new String("This is a string object.");  
  
document.write(typeof strLit);  
document.write("<br/>");  
document.write(typeof strObj);  
// Output:  
// string  
// object  
```  
  
## <a name="methods-for-string-literals"></a>Методы для строковых литералов  
 При вызове метода для строкового литерала он временно преобразуется в объект-оболочку строки. Строковый литерал обрабатывается так, как будто он создан с помощью оператора `new`.  
  
 В следующем примере метод `toUpperCase` применяется к строковому литералу.  
  
```JavaScript  
var strLit = "This is a string literal.";  
  
var result1 = strLit.toUpperCase();  
  
var result2 = (new String(strLit)).toUpperCase();  
  
document.write(result1);  
document.write("<br/>");  
document.write(result2);  
// Output:   
// THIS IS A STRING LITERAL.  
// THIS IS A STRING LITERAL.  
```  
  
## <a name="accessing-an-individual-character"></a>Доступ к отдельному символу  
 Доступ к отдельному символу строки осуществляется через доступное только для чтения индексированное свойство массива. Эта функция появилась в [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)]. В следующем примере осуществляется доступ к отдельным символам строки.  
  
```JavaScript  
var str = "abcd";  
var result = str[2];  
document.write (result);  
// Output: c  
  
var result = "the"[0];  
document.write(result);  
// Output: t  
```  
  
## <a name="requirements"></a>Требования  
 `String Object` появился в [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)]. Некоторые члены в следующих списках были введены в более поздних версиях.  
  
<a name="js56jsobjstringprop"></a>   
## <a name="properties"></a>Свойства  
 В следующей таблице перечислены свойства объекта `String`.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|[Свойство constructor](../../javascript/reference/constructor-property-string.md)|Указывает функцию, которая создает объект.|  
|[Свойство length (строка)](../../javascript/reference/length-property-string-javascript.md)|Возвращает длину объекта `String`.|  
|[Свойство prototype](../../javascript/reference/prototype-property-string.md)|Возвращает ссылку на прототип класса объектов.|  
  
## <a name="functions"></a>Функции  
 В следующей таблице перечислены функции объекта `String`.  
  
|Функция|Описание|  
|--------------|-----------------|  
|[Функция String.fromCharCode](../../javascript/reference/string-fromcharcode-function-javascript.md)|Возвращает строку, содержащую набор значений знаков Юникода.|  
|[Функция String.fromCodePoint](../../javascript/reference/string-fromcodepoint-function-javascript.md)|Возвращает строку, связанную с кодовой точкой Юникода UTF-16.|  
|[Функция String.raw](../../javascript/reference/string-raw-function-javascript.md)|Возвращает необработанную строковую форму строки шаблона.|  
  
<a name="js56jsobjstringmeth"></a>   
## <a name="methods"></a>Методы  
 В следующей таблице перечислены методы объекта `String`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Метод Anchor](../../javascript/reference/html-tag-methods-javascript.md)|Задает привязку HTML, которая имеет в тексте атрибут NAME.|  
|[Метод Big](../../javascript/reference/html-tag-methods-javascript.md)|Помещает HTML \<BIG > теги вокруг текста.|  
|[Метод blink](../../javascript/reference/html-tag-methods-javascript.md)|Помещает HTML \<BLINK > теги вокруг текста.|  
|[Метод bold](../../javascript/reference/html-tag-methods-javascript.md)|Помещает HTML \<B > теги вокруг текста.|  
|[Метод charAt](../../javascript/reference/charat-method-string-javascript.md)|Возвращает знак с указанным индексом.|  
|[Метод charCodeAt](../../javascript/reference/charcodeat-method-string-javascript.md)|Возвращает код Юникода для указанного знака.|  
|[Метод codePointAt](../../javascript/reference/codepointat-method-string-javascript.md)|Возвращает кодовую точку для символа Юникода UTF-16.|  
|[Метод concat (строка)](../../javascript/reference/concat-method-string-javascript.md)|Возвращает строку, содержащую результат объединения двух указанных строк.|  
|[Метод endsWith](../../javascript/reference/endswith-method-string-javascript.md)|Возвращает логическое значение, указывающее, заканчивается ли строка или подстрока переданной строкой.|  
|[Метод includes](../../javascript/reference/includes-method-string-javascript.md)|Возвращает логическое значение, указывающее, содержится ли переданная строка в объекте String.|  
|[Метод fixed](../../javascript/reference/html-tag-methods-javascript.md)|Помещает HTML \<TT > теги вокруг текста.|  
|[Метод fontcolor](../../javascript/reference/html-tag-methods-javascript.md)|Помещает HTML \<ШРИФТА > тегов с атрибутом COLOR вокруг текста.|  
|[Метод fontsize](../../javascript/reference/html-tag-methods-javascript.md)|Помещает HTML \<ШРИФТА > тегов с атрибутом SIZE вокруг текста.|  
|[Метод hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Возвращает логическое значение, указывающее, содержит ли объект свойство с указанным именем.|  
|[Метод indexOf (строка)](../../javascript/reference/indexof-method-string-javascript.md)|Возвращает позицию символа первого вхождения подстроки в строку.|  
|[Метод isPrototypeOf](../../javascript/reference/isprototypeof-method-object-javascript.md)|Возвращает логическое значение, указывающее, существует ли объект в другом объекте цепочки прототипов.|  
|[Метод italics](../../javascript/reference/html-tag-methods-javascript.md)|Помещает HTML \<я > теги вокруг текста.|  
|[Метод lastIndexOf (строка)](../../javascript/reference/lastindexof-method-string-javascript.md)|Возвращает последнее вхождение подстроки в строку.|  
|[Метод link](../../javascript/reference/html-tag-methods-javascript.md)|Заключает текст в привязку HTML, имеющую атрибут HREF.|  
|[Метод localeCompare](../../javascript/reference/localecompare-method-string-javascript.md)|Возвращает значение, указывающее, одинаковый ли язык у двух строк.|  
|[Метод match](../../javascript/reference/match-method-string-javascript.md)|Поиск по строке, используя указанный **регулярное выражение** объекта и возвращает результаты в виде массива.|  
|[Метод normalize](../../javascript/reference/normalize-method-string-javascript.md)|Возвращает форму нормализации Юникода для указанной строки.|  
|[Метод propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Возвращает логическое значение, определяющее, является ли указанное свойство частью объекта, и является ли оно перечислимым.|  
|[Метод Repeat](../../javascript/reference/repeat-method-string-javascript.md)|Возвращает новый объект string со значением, равным исходной строке, повторенной указанное число раз.|  
|[Метод replace](../../javascript/reference/replace-method-string-javascript.md)|С помощью регулярного выражения заменяет текст в строке и возвращает результат.|  
|[Метод search](../../javascript/reference/search-method-string-javascript.md)|Возвращает позицию первой найденной подстроки, совпадающей с регулярным выражением.|  
|[Метод slice (строка)](../../javascript/reference/slice-method-string-javascript.md)|Возвращает фрагмент строки.|  
|[Метод small](../../javascript/reference/html-tag-methods-javascript.md)|Помещает HTML \<SMALL > теги вокруг текста.|  
|[Метод split](../../javascript/reference/split-method-string-javascript.md)|Возвращает массив строк, являющийся результатом разделения строки на подстроки.|  
|[Метод startsWith](../../javascript/reference/startswith-method-string-javascript.md)|Возвращает логическое значение, указывающее, начинается ли строка или подстрока с переданной строки.|  
|[Метод strike](../../javascript/reference/html-tag-methods-javascript.md)|Помещает HTML \<STRIKE > теги вокруг текста.|  
|[Метод sub](../../javascript/reference/html-tag-methods-javascript.md)|Помещает HTML \<SUB > теги вокруг текста.|  
|[Метод substr](../../javascript/reference/substr-method-string-javascript.md)|Возвращает подстроку указанной длины, которая начинается с указанной позиции.|  
|[Метод substring](../../javascript/reference/substring-method-string-javascript.md)|Возвращает подстроку, расположенную в указанном месте объекта `String`.|  
|[Метод sup](../../javascript/reference/html-tag-methods-javascript.md)|Помещает HTML \<SUP > теги вокруг текста.|  
|[Метод toLocaleLowerCase](../../javascript/reference/tolocalelowercase-method-string-javascript.md)|Возвращает строку, в которой все буквенные символы преобразованы в нижний регистр с учетом текущего языкового стандарта хост-среды.|  
|[Метод toLocaleString](../../javascript/reference/tolocalestring-method-object-javascript.md)|Возвращает объект, преобразованный в строку с учетом текущего языкового стандарта.|  
|[Метод toLocaleUpperCase](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)|Возвращает строку, в которой все буквенные символы преобразованы в верхний регистр с учетом текущего языкового стандарта хост-среды.|  
|[Метод toLowerCase](../../javascript/reference/tolowercase-method-javascript.md)|Возвращает строку, в которой все буквенные символы преобразованы в нижний регистр.|  
|[Метод toString](../../javascript/reference/tostring-method-string-1.md)|Возвращает строку.|  
|[Метод toUpperCase](../../javascript/reference/touppercase-method-string-javascript.md)|Возвращает строку, в которой все буквенные символы преобразованы в верхний регистр.|  
|[Метод trim](../../javascript/reference/trim-method-string-javascript.md)|Возвращает строку с удаленными начальными и конечными символами пробела и маркером конца строки.|  
|[Метод valueOf](../../javascript/reference/valueof-method-string.md)|Возвращает строку.|  
  
## <a name="see-also"></a>См. также  
 [Оператор new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Прокрутки, сдвига и масштабирования примера приложения](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)