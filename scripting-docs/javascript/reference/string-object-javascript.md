---
title: "Объект String (JavaScript) | Microsoft Docs"
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
  - "String_JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "String - объект"
  - "String - объект, общие сведения"
ms.assetid: 8063ecd5-5778-4e87-b985-b21420171914
caps.latest.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 32
---
# Объект String (JavaScript)
Позволяет управлять текстовыми строками, форматировать их и выполнять поиск подстрок в строках.  
  
## Синтаксис  
  
```  
  
newString = new String(["stringLiteral"])  
```  
  
## Параметры  
 `newString`  
 Обязательный.  Имя переменной, которой присваивается объект `String`.  
  
 `stringLiteral`  
 Необязательный.  Любая группа символов Юникода.  
  
## Заметки  
 Для добавления символов, которые нельзя ввести напрямую, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] позволяет добавлять в строки специальные escape\-последовательности.  Например, `\t` обозначает символ табуляции.  Дополнительные сведения см. в статье [Специальные символы](../../javascript/advanced/special-characters-javascript.md).  
  
## Строковые литералы  
 *Строковый литерал* представляет собой нуль или более символов, заключенных в одинарные или двойные кавычки.  Строковый литерал содержит основной \(примитивный\) тип данных из `string`.  *Объект String* создается с помощью [оператора new](../../javascript/reference/new-operator-decrementjavascript.md) и имеет тип данных `Object`.  
  
 В следующем примере показано, что типы данных строкового литерала и объекта `String` не совпадают.  
  
```javascript  
var strLit = "This is a string literal.";  
var strObj = new String("This is a string object.");  
  
document.write(typeof strLit);  
document.write("<br/>");  
document.write(typeof strObj);  
// Output:  
// string  
// object  
```  
  
## Методы для строковых литералов  
 Метод, вызываемый для строкового литерала, временно преобразуется в объект\-оболочку строки.  Строковый литерал обрабатывается так, как будто для его создания использовался оператор `new`.  
  
 В следующем примере к строковому литералу применяется метод `toUpperCase`.  
  
```javascript  
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
  
## Получение доступа к отдельному символу  
 С отдельным символом строки можно работать как с индексированным свойством массива, доступным только для чтения.  Данная возможность впервые появилась в [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)].  Следующий пример демонстрирует обращение к отдельным символам строки.  
  
```javascript  
var str = "abcd";  
var result = str[2];  
document.write (result);  
// Output: c  
  
var result = "the"[0];  
document.write(result);  
// Output: t  
```  
  
## Требования  
 `String Object` появился в [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)].  Некоторые члены из следующих списков были представлены в более поздних версиях.  
  
<a name="js56jsobjstringprop"></a>   
## Свойства  
 В следующей таблице перечислены свойства объекта `String`.  
  
|Свойство|Описание|  
|--------------|--------------|  
|[Свойство constructor](../../javascript/reference/constructor-property-string.md)|Указывает функцию, которая создает объект.|  
|[Свойство length \(String\)](../../javascript/reference/length-property-string-javascript.md)|Возвращает длину объекта `String`.|  
|[Свойство prototype](../../javascript/reference/prototype-property-string.md)|Возвращает ссылку на прототип класса объектов.|  
  
## Функции  
 В следующей таблице перечислены функции объекта `String`.  
  
|Функция|Описание|  
|-------------|--------------|  
|[Функция String.fromCharCode](../../javascript/reference/string-fromcharcode-function-javascript.md)|Возвращает строку, содержащую набор значений символов Юникода.|  
|[Функция String.fromCodePoint](../../javascript/reference/string-fromcodepoint-function-javascript.md)|Возвращает строку, связанную с кодовой точкой Юникода UTF\-16.|  
|[Функция String.raw](../../javascript/reference/string-raw-function-javascript.md)|Возвращает необработанную строковую форму строки шаблона.|  
  
<a name="js56jsobjstringmeth"></a>   
## Методы  
 В следующей таблице перечислены методы объекта `String`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Метод anchor](../../javascript/reference/html-tag-methods-javascript.md)|Заключает текст в привязку HTML, имеющую атрибут NAME.|  
|[Метод big](../../javascript/reference/html-tag-methods-javascript.md)|Заключает текст в HTML\-теги \<BIG\>.|  
|[Метод blink](../../javascript/reference/html-tag-methods-javascript.md)|Заключает текст в HTML\-теги \<BLINK\>.|  
|[Метод bold](../../javascript/reference/html-tag-methods-javascript.md)|Заключает текст в HTML\-теги \<B\>.|  
|[Метод charAt](../../javascript/reference/charat-method-string-javascript.md)|Возвращает символ по указанному индексу.|  
|[Метод charCodeAt](../../javascript/reference/charcodeat-method-string-javascript.md)|Возвращает код Юникода для указанного символа.|  
|[Метод codePointAt](../../javascript/reference/codepointat-method-string-javascript.md)|Возвращает кодовую точку для символа Юникода UTF\-16.|  
|[Метод concat \(String\)](../../javascript/reference/concat-method-string-javascript.md)|Возвращает строку, содержащую результат объединения двух предоставленных строк.|  
|[Метод endsWith](../../javascript/reference/endswith-method-string-javascript.md)|Возвращает логическое значение, указывающее, заканчивается ли строка или подстрока переданной строкой.|  
|[Метод includes](../../javascript/reference/includes-method-string-javascript.md)|Возвращает логическое значение, указывающее, содержится ли переданная строка в объекте String.|  
|[Метод fixed](../../javascript/reference/html-tag-methods-javascript.md)|Заключает текст в HTML\-теги \<TT\>.|  
|[Метод fontcolor](../../javascript/reference/html-tag-methods-javascript.md)|Заключает текст в HTML\-теги \<FONT\> с атрибутом COLOR.|  
|[Метод fontsize](../../javascript/reference/html-tag-methods-javascript.md)|Заключает текст в HTML\-теги \<FONT\> с атрибутом SIZE.|  
|[Метод hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Возвращает логическое значение, указывающее, содержит ли объект свойство с указанным именем.|  
|[Метод indexOf \(String\)](../../javascript/reference/indexof-method-string-javascript.md)|Возвращает позицию символа первого вхождения подстроки в строке.|  
|[Метод isPrototypeOf](../../javascript/reference/isprototypeof-method-object-javascript.md)|Возвращает логическое значение, указывающее, существует ли объект в цепочке прототипов другого объекта.|  
|[Метод italics](../../javascript/reference/html-tag-methods-javascript.md)|Заключает текст в HTML\-теги \<I\>.|  
|[Метод lastIndexOf \(String\)](../../javascript/reference/lastindexof-method-string-javascript.md)|Возвращает последнее вхождение подстроки в строке.|  
|[Метод link](../../javascript/reference/html-tag-methods-javascript.md)|Заключает текст в привязку HTML, имеющую атрибут HREF.|  
|[Метод localeCompare](../../javascript/reference/localecompare-method-string-javascript.md)|Возвращает значение, указывающее, эквивалентны ли две строки в текущем языковом стандарте.|  
|[Метод match](../../javascript/reference/match-method-string-javascript.md)|Возвращает в виде массива результаты поиска строки с использованием предоставленного объекта **Regular Expression**.|  
|[Метод normalize](../../javascript/reference/normalize-method-string-javascript.md)|Возвращает форму нормализации Юникода для указанной строки.|  
|[Метод propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Возвращает логическое значение, определяющее, является ли указанное свойство частью объекта, и является ли оно перечислимым.|  
|[Метод repeat](../../javascript/reference/repeat-method-string-javascript.md)|Возвращает новый объект string со значением, равным исходной строке, повторенной указанное число раз.|  
|[Метод replace](../../javascript/reference/replace-method-string-javascript.md)|Заменяет текст в строке с помощью регулярного выражения и возвращает результат.|  
|[Метод search](../../javascript/reference/search-method-string-javascript.md)|Возвращает позицию первой найденной подстроки, совпадающей с регулярным выражением.|  
|[Метод slice \(String\)](../../javascript/reference/slice-method-string-javascript.md)|Возвращает фрагмент строки.|  
|[Метод small](../../javascript/reference/html-tag-methods-javascript.md)|Заключает текст в HTML\-теги \<SMALL\>.|  
|[Метод split](../../javascript/reference/split-method-string-javascript.md)|Возвращает массив строк, являющийся результатом разделения строки на подстроки.|  
|[Метод startsWith](../../javascript/reference/startswith-method-string-javascript.md)|Возвращает логическое значение, указывающее, начинается ли строка или подстрока с переданной строки.|  
|[Метод strike](../../javascript/reference/html-tag-methods-javascript.md)|Заключает текст в HTML\-теги \<STRIKE\>.|  
|[Метод sub](../../javascript/reference/html-tag-methods-javascript.md)|Заключает текст в HTML\-теги \<SUB\>.|  
|[Метод substr](../../javascript/reference/substr-method-string-javascript.md)|Возвращает подстроку указанной длины, начиная с указанной позиции.|  
|[Метод substring](../../javascript/reference/substring-method-string-javascript.md)|Возвращает подстроку, расположенную в указанном месте объекта `String`.|  
|[Метод sub](../../javascript/reference/html-tag-methods-javascript.md)|Заключает текст в HTML\-теги \<SUP\>.|  
|[Метод toLocaleLowerCase](../../javascript/reference/tolocalelowercase-method-string-javascript.md)|Возвращает строку, в которой все буквенные символы преобразованы в нижний регистр с учетом текущего языкового стандарта среды размещения.|  
|[Метод toLocaleString](../../javascript/reference/tolocalestring-method-object-javascript.md)|Возвращает объект, преобразованный в строку с использованием текущего языкового стандарта.|  
|[Метод toLocaleUpperCase](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)|Возвращает строку, в которой все буквенные символы преобразованы в верхний регистр с учетом текущего языкового стандарта среды размещения.|  
|[Метод toLowerCase](../../javascript/reference/tolowercase-method-javascript.md)|Возвращает строку, в которой все буквенные символы преобразованы в нижний регистр.|  
|[Метод toString](../../javascript/reference/tostring-method-string-1.md)|Возвращает строку.|  
|[Метод toUpperCase](../../javascript/reference/touppercase-method-string-javascript.md)|Возвращает строку, в которой все буквенные символы преобразованы в верхний регистр.|  
|[Метод trim](../../javascript/reference/trim-method-string-javascript.md)|Возвращает строку с удаленными начальными и конечными пробелами и символами конца строки.|  
|[Метод valueOf](../../javascript/reference/valueof-method-string.md)|Возвращает строку.|  
  
## См. также  
 [Оператор new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Пример приложения с функциями прокрутки, сдвига и масштабирования](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)