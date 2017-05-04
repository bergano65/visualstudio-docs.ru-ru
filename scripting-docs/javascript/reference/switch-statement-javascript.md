---
title: "Оператор switch (JavaScript) | Microsoft Docs"
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
  - "switch_JavaScriptKeyword"
  - "default_JavaScriptKeyword"
  - "case_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "switch - оператор"
ms.assetid: 61f80e8b-3739-4146-a893-c2832d92b28c
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Оператор switch (JavaScript)
Обеспечивает выполнение одного или нескольких операторов, если значение указанного выражения совпадает с меткой.  
  
## Синтаксис  
  
```  
switch (expression) {  
    case label :  
        statementlist  
    case label :  
    default :  
        statementlist  
}   
```  
  
## Параметры  
 `expression`  
 Вычисляемое выражение.  
  
 `label`  
 Идентификатор, с которым сравнивается `expression`.  Если `label` является `expression`, выполнение начинается со `statementlist`сразу после двоеточия и продолжается либо до оператора `break` \(он не является обязательным\), либо до конца оператора `switch`.  
  
 `statementlist`  
 Один или несколько операторов для выполнения.  
  
## Заметки  
 Используйте предложение `default`, чтобы предоставить оператор для выполнения в том случае, если ни одна из меток не совпадает с выражением `expression`.  Предложение может находиться в любом месте блока кода `switch`.  
  
 Можно указать ноль или более блоков `label`.  Если ни одна метка `label` не совпадает со значением выражения `expression`, а предложение `default` отсутствует, операторы не выполняются.  
  
 Выполнение оператора `switch` происходит следующим образом.  
  
-   Вычисление `expression` и перебор подписей `label` по порядку до тех пор, пока не будет найдено совпадение.  
  
-   Если значение `label` равно `expression`, выполняется соответствующий `statementlist`.  
  
     Продолжение выполнения до обнаружения оператора `break` или до завершения оператора `switch`.  Это означает выполнение нескольких блоков `label`, если оператор `break` не используется.  
  
-   Если `label` не равно `expression`, переход к случаю `default`.  Если случая `default` нет, выполняется переход к последнему шагу.  
  
-   Продолжение выполнения с оператора, следующего за окончанием блока кода `switch`.  
  
## Пример  
 В следующем примере проверяется тип объекта.  
  
```javascript  
function MyObjectType(obj) {  
    switch (obj.constructor) {  
        case Date:  
            document.write("Object is a Date.");  
            break;  
        case Number:  
            document.write("Object is a Number.");  
            break;  
        case String:  
            document.write("Object is a String.");  
            break;  
        default:  
            document.write("Object is unknown.");  
    }  
}  
  
// Output when obj is a Date:  
// Object is a Date.  
  
// Output when obj is a Number:  
// Object is a Number.  
  
// Output when obj is a String:  
// Object is a String.  
  
// Output when obj is something other than a Date, Number, or String:  
// Object is unknown.  
  
```  
  
## Пример  
 В следующем примере кода показано, что происходит, если не использовать оператор `break`.  
  
```javascript  
function MyObjectType(obj) {  
    switch (obj.constructor) {  
        case Date:  
            document.write("Object is a Date.");  
        case Number:  
            document.write("Object is a Number.");  
        case String:  
            document.write("Object is a String.");  
        default:  
            document.write("Object is unknown.");  
    }  
}  
  
// Output when obj is a Date:  
// Object is a Date.Object is a Number.Object is a String.Object is unknown.  
  
// Output when obj is a Number:  
// Object is a Number.Object is a String.Object is unknown.  
  
// Output when obj is a String:  
// Object is a String.Object is unknown.  
  
// Output when obj is something other than a Date, Number, or String:  
// Object is unknown.  
  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## См. также  
 [Оператор break](../../javascript/reference/break-statement-javascript.md)   
 [Оператор if...else](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)