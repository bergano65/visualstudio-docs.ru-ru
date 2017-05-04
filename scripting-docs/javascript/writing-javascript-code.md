---
title: "Написание кода JavaScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.htmldesigner.html"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "код, синтаксис JavaScript"
  - "комментарии, код JavaScript"
  - "код JavaScript"
ms.assetid: dde28266-0d0f-4460-a819-f931cf0911ad
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Написание кода JavaScript
Как и во многих других языках программирования, код [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] состоит из операторов, блоков, содержащих связанные наборы операторов, и комментариев.  В операторах можно использовать переменные, строки, числа и выражения.  
  
## Операторы  
 Программа на [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] представляет собой коллекцию операторов.  Операторы [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] объединяют выражения таким образом, чтобы они выполняли одну общую задачу.  
  
 Оператор состоит из одного или нескольких выражений, ключевых слов или операторов \(символов\).  Обычно оператор записывается на одной строке, хотя оператор может быть записан и над двух или более строках.  Кроме того, два и более операторов можно записать на одной строке, разделяя их точкой с запятой.  Обычно каждая новая строка начинает новый оператор.  Рекомендуется завершать операторы явным образом.  Для этого используется точка с запятой \(;\), являющаяся символом завершения операторов [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
 Далее показаны два примера операторов [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  Текст после символов \/\/ представляет собой *комментарии*, служащие для пояснения программы.  
  
```javascript  
var aBird = "Robin"; // Assign the text "Robin" to the variable aBird.  
var today = new Date(); // Assign today's date to the variable today.  
```  
  
 Группа операторов [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], заключенных в фигурные скобки \({}\), называется *блоком*.  В общем, операторы, объединенные в блок, можно рассматривать как один оператор.  Это означает, что блоки можно использовать в любых местах, где [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] требует одного оператора.  В качестве известных исключений можно привести заголовки циклов **for** и `while`.  Следует отметить, что отдельные операторы в блоке заканчиваются точкой с запятой, но сам блок — нет.  
  
 Как правило, блоки используются в функциях и условных выражениях.  Следует помнить, что в отличие от C\+\+ и некоторых других языков, блок в [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] не считается новой областью; новую область создают только функции.  
  
 В следующем примере предложение `else` содержит блок из двух операторов, заключенных в фигурные скобки.  Блок обрабатывается как один оператор.  Кроме того, сама функция состоит из блока операторов, заключенных в фигурные скобки.  Операторы под функцией находятся вне блока и, следовательно, не являются частью определения функции.  
  
```javascript  
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
  
## Комментарии  
 Комментарий [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], состоящий из одной строки, начинается с двух знаков косой черты \(\/\/\).  Ниже приведен пример комментария, состоящего из одной строки.  
  
```javascript  
var aGoodIdea = "Comment your code thoroughly."; // This is a single-line comment.  
```  
  
 Комментарий [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], состоящий из нескольких строк, начинается с косой черты и звездочки \(\/\*\), а заканчивается этими же знаками, стоящими в обратном порядке \(\*\/\).  
  
```javascript  
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
>  При попытке вставить один многострочный комментарий внутрь другого результат будет обработан в [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] неожиданным образом.  Знаки \*\/, означающие конец внутреннего многострочного комментария, будут считаться концом всего многострочного комментария.  Это означает, что текст, следующий за вложенным многострочным комментарием, не будет считаться комментарием; вместо этого он будет интерпретироваться как код [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] и вызовет синтаксические ошибки.  
  
 Рекомендуется писать все комментарии как блоки однострочных комментариев.  Это позволяет переносить в комментарии крупные сегменты кода с помощью многострочных комментариев на более поздних этапах.  
  
```javascript  
// This is another multiline comment, written as a series of single-line comments.  
// After the statement is executed, you can refer to the content of the   
// aGoodIdea variable by using its name.  
var extendedIdea = aGoodIdea + " You never know when you'll have to figure out what it does.";  
```  
  
## Присваивания и равенство  
 Знак равенства \(\=\) используется в операторах [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] для присваивания значений переменным — это оператор присваивания.  Левый операнд оператора "\=" всегда является левосторонним значением.  Примеры левосторонних значений:  
  
-   переменные;  
  
-   элементы массива;  
  
-   свойства объекта.  
  
 Правый операнд оператора "\=" всегда является правосторонним значением.  Правосторонние значения могут быть произвольным значением любого типа, включая значение выражения.  Ниже приведен пример оператора присваивания в [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```javascript  
var anInteger = 3;  
```  
  
 Компилятор [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] интерпретирует этот оператор следующим образом: "присвоить значение 3 переменной **anInteger**" или "переменная **anInteger** принимает значение 3".  
  
 Обратите внимание на разницу между оператором "\=" \(присваивание\) и оператором "\=\=" \(равенство\).  Если требуется сравнить два значения, чтобы определить, равны ли они, используйте два знака равенства \(\=\=\).  Подробно это обсуждается в разделе [Управление выполнением программ](../javascript/controlling-program-flow-javascript.md).  
  
## Выражения  
 Значение выражения [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] может быть любого допустимого типа [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] — число, строка, объект и т. д.  Простейшими выражениями являются литералы.  Ниже приведены некоторые примеры литеральных выражений [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```javascript  
3.9                       // numeric literal  
"Hello!"                  // string literal  
false                     // boolean literal  
null                      // literal null value  
{x:1, y:2}                // Object literal  
[1,2,3]                   // Array literal  
function(x){return x*x;}  // function literal  
```  
  
 Более сложные выражения могут содержать переменные, вызовы функций и другие выражения.  Для объединения выражений и создания сложных выражений можно использовать операторы.  Примеры операторов: `+` \(сложение\), `-` \(вычитание\), `*` \(умножение\) и `/` \(деление\).  
  
 Ниже приведены некоторые примеры сложных выражений [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```javascript  
var anExpression = 3 * (4 / 5) + 6;  
var aSecondExpression = Math.PI * radius * radius;  
var aThirdExpression = aSecondExpression + "%" + anExpression;  
var aFourthExpression = "(" + aSecondExpression + ") % (" + anExpression + ")";  
```