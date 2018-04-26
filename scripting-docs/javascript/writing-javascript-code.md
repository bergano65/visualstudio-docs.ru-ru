---
title: Написание кода JavaScript | Документы Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.htmldesigner.html
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- code, JavaScript syntax
- comments, JavaScript code
- JavaScript code
ms.assetid: dde28266-0d0f-4460-a819-f931cf0911ad
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e50bc25f818724b59d9adda51f97d76ae14de2b4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="writing-javascript-code"></a>Написание кода JavaScript
Как и многие другие языки программирования, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] организован в виде операторов, блоков, состоящих из связанных наборов операторов, а также комментариев. Внутри оператора можно использовать переменные, строки, числа и выражения.  
  
## <a name="statements"></a>Операторы  
 Программа [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] представляет собой коллекцию операторов. Операторы [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] объединяют выражения таким образом, чтобы они выполняли единую задачу.  
  
 Оператор состоит из одного или нескольких выражений, ключевых слов или операторов (символов). Как правило, оператор записывается на одной строке, хотя он может занимать две и более строк. Кроме того, несколько операторов можно записать на одной строке, разделяя их точкой с запятой. Обычно каждый новый оператор начинается с новой строки. Рекомендуется завершать операторы явным образом. Для этого в [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] служит точка с запятой (;).  
  
 Ниже приведены два примера операторов [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]. Операторы после символов // являются *комментариями*, то есть поясняющими замечаниями в программе.  
  
```JavaScript  
var aBird = "Robin"; // Assign the text "Robin" to the variable aBird.  
var today = new Date(); // Assign today's date to the variable today.  
```  
  
 Группа операторов [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], заключенных в фигурные скобки ({}), называется *блоком*. Сгруппированные в блок операторы обычно можно рассматривать как единый оператор. Это означает, что блоки можно использовать в большинстве мест, где [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] ожидает отдельный оператор. Здесь следует отметить важные исключения — заголовки циклов **for** и `while`. Обратите внимание, что отдельные операторы в блоке заканчиваются точкой с запятой, а сам блок — нет.  
  
 Блоки обычно используются в функциях и условных выражениях. Обратите внимание, что, в отличие от C++ и некоторых других языков, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] не считает блок новой областью. Новую область создают только функции.  
  
 В следующем примере предложение `else` содержит блок из двух операторов, заключенных в фигурные скобки. Этот блок обрабатывается как единый оператор. Кроме того, сама функция состоит из блока операторов, заключенных в фигурные скобки. Операторы под функцией выходят за пределы блока и поэтому не являются частью определения функции.  
  
```JavaScript  
function inchestometers(inches)  
   {  
   if (inches < 0)  
      return -1;  
   else  
      {  
      var meters = inches / 39.37;  
      return meters;  
      }  
   }  
  
var inches = 12;  
var meters = inchestometers(inches);  
document.write("the value in meters is " + meters);  
```  
  
## <a name="comments"></a>Комментарии  
 Однострочный комментарий [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] начинается с пары символов косой черты (//). Ниже приведен пример однострочного комментария.  
  
```JavaScript  
var aGoodIdea = "Comment your code thoroughly."; // This is a single-line comment.  
```  
  
 Многострочный комментарий [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] начинается с косой черты и звездочки (/\*) и заканчивается этими же символами, стоящими в обратном порядке (\*/).  
  
```JavaScript  
/*  
This is a multiline comment that explains the preceding code statement.  
  
The statement assigns a value to the aGoodIdea variable. The value,   
which is contained between the quote marks, is called a literal. A   
literal explicitly and directly contains information; it does not   
refer to the information indirectly. The quote marks are not part   
of the literal.  
*/  
```  
  
> [!NOTE]
>  При попытке вставить один многострочный комментарий в другой [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] интерпретирует итоговый многострочный комментарий непредсказуемым образом. Символы */, обозначающие конец внутреннего многострочного комментария, интерпретируются как конец всего комментария. Это означает, что текст, следующий за внутренним многострочным комментарием, не будет закомментирован. Вместо этого он будет интерпретирован как код [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], что приведет к синтаксическим ошибкам.  
  
 Рекомендуется писать все комментарии в виде блоков однострочных комментариев. Позже это позволит закомментировать крупные сегменты кода с помощью многострочных комментариев.  
  
```JavaScript  
// This is another multiline comment, written as a series of single-line comments.  
// After the statement is executed, you can refer to the content of the   
// aGoodIdea variable by using its name.  
var extendedIdea = aGoodIdea + " You never know when you'll have to figure out what it does.";  
```  
  
## <a name="assignments-and-equality"></a>Присваивания и равенство  
 Знак равенства (=) используется в операторах [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] для присвоения значений переменным — это оператор присваивания. Левый операнд оператора = всегда является левосторонним значением. Примеры левосторонних значений:  
  
-   переменные;  
  
-   элементы массива;  
  
-   свойства объекта.  
  
 Правый операнд оператора = всегда является правосторонним значением. Правосторонние значения могут быть произвольным значением любого типа, включая значение выражения. Ниже приведен пример оператора присваивания [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```JavaScript  
var anInteger = 3;  
```  
  
 Компилятор [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] интерпретирует этот оператор следующим образом: "присвоить значение 3 переменной **anInteger**" или "**anInteger** принимает значение 3".  
  
 Вам нужно понимать разницу между оператором = (присваивание) и оператором == (равенство). Если вы хотите сравнить два значения, чтобы определить, равны ли они, используйте два знака равенства (==). Это подробно рассмотрено в разделе [Управление выполнением программы](../javascript/controlling-program-flow-javascript.md).  
  
## <a name="expressions"></a>Выражения  
 Значение выражения [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] может иметь любой допустимый тип [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] — число, строка, объект и т. д. Простейшими выражениями являются литералы. Ниже приведено несколько примеров литеральных выражений [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```JavaScript  
3.9                       // numeric literal  
"Hello!"                  // string literal  
false                     // boolean literal  
null                      // literal null value  
{x:1, y:2}                // Object literal  
[1,2,3]                   // Array literal  
function(x){return x*x;}  // function literal  
```  
  
 Более сложные выражения могут содержать переменные, вызовы функций и другие выражения. Вы можете комбинировать выражения, чтобы создавать более сложные выражения, с помощью операторов. Примеры операторов: `+` (сложение), `-` (вычитание), `*` (умножение) и `/` (деление).  
  
 Ниже приведено несколько примеров сложных выражений [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```JavaScript  
var anExpression = 3 * (4 / 5) + 6;  
var aSecondExpression = Math.PI * radius * radius;  
var aThirdExpression = aSecondExpression + "%" + anExpression;  
var aFourthExpression = "(" + aSecondExpression + ") % (" + anExpression + ")";  
```