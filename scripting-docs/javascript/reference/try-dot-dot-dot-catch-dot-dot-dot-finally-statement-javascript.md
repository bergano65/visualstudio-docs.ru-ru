---
title: "Оператор try...catch...finally (JavaScript) | Microsoft Docs"
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
  - "try_JavaScriptKeyword"
  - "finally_JavaScriptKeyword"
  - "catch_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "обработка исключений try-catch"
  - "обработка исключений try-catch, сведения об обработке исключений try-catch"
  - "обработка исключений try-catch, catch - блок"
  - "обработка исключений try-catch, finally - блок"
ms.assetid: b7a0a54e-dfaa-4e41-bf25-bcaa43e601fb
caps.latest.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 28
---
# Оператор try...catch...finally (JavaScript)
Настраивает блоки кода, в которых ошибки, возникшие в одном блоке, обрабатываются в другом.  Ошибки, возникающие в блоке `try`, перехватываются в блоке `catch`.  [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Синтаксис  
  
```  
try {  
    tryStatements  
}  
catch(exception){  
    catchStatements  
}  
finally {  
    finallyStatements  
}  
```  
  
## Параметры  
 `tryStatements`  
 Обязательный.  Операторы, в которых может возникнуть ошибка.  
  
 `exception`  
 Обязательный.  Любое имя переменной.  Начальное значение аргумента `exception` — это значение возникшей ошибки.  
  
 `catchStatements`  
 Необязательный.  Операторы обработки ошибок, возникающих в связанном блоке `tryStatements`.  
  
 `finallyStatements`  
 Необязательный.  Операторы, безусловно выполняемые после выполнения всех остальных действий по обработке ошибки.  
  
## Заметки  
 Оператор `try...catch...finally` позволяет обрабатывать некоторые или все ошибки, которые могут возникнуть в том или ином блоке кода, не прерывая выполнение этого кода.  Если возникают ошибки, которые не обрабатываются, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] выдает обычное сообщение об ошибке.  
  
 Блок `try` содержит код, который может спровоцировать ошибку, а блок `catch` — код, который обрабатывает некоторые или все ошибки.  Если в блоке `try` возникает ошибка, управление программой передается блоку `catch`.  Значение `exception` — это значение ошибки, возникшей в блоке `try`.  Если ошибок нет, код в блоке `catch` не выполняется.  
  
 С помощью оператора `throw` можно передать ошибку на следующий уровень для повторного создания ошибки.  
  
 После того как в блоке `try` будут выполнены все операторы, а в блоке `catch` завершится обработка ошибок, выполняются операторы в блоке `finally` \(независимо от того, обработана ли ошибка\).  Код в блоке `finally` выполняется всегда, если нет необработанных ошибок \(например, если в блоке **catch** возникает ошибка времени выполнения\).  
  
## Пример  
 В следующем примере создается исключение `ReferenceError` и отображается имя и текст ошибки.  
  
```javascript  
try {  
    addalert("bad call");  
}  
catch(e) {  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF);  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
  
// Output:  
Error Message: 'addalert' is undefined  
Error Code: 5009  
Error Name: ReferenceError  
  
```  
  
## Пример  
 В следующем примере показано повторное создание ошибок и выполнение вложенных блоков `try…catch`.  Если ошибка создана во вложенном блоке `try`, она передается во вложенный блок `catch`, который создает ее повторно.  Вложенный блок `finally` выполняется до того, как внешний блок `catch` обработает ошибку, а в конце выполняется внешний блок `finally`.  
  
```javascript  
try {  
    document.write("Outer try running...<br/>");  
  
    try {  
        document.write("Nested try running...<br/>");  
        throw new Error(301, "an error");  
    }  
    catch (e) {  
        document.write ("Nested catch caught " + e.message + "<br/>");  
        throw e;  
    }  
    finally {  
        document.write ("Nested finally is running...<br/>");  
    }  
}  
catch (e) {  
    document.write ("Outer catch caught " + e.message + "<br/>");  
}  
finally {  
    document.write ("Outer finally running");  
}  
  
// Output:  
// Outer try running...  
// Nested try running...  
// Nested catch caught error from nested try  
// Nested finally is running...  
// Outer catch caught error from nested try  
// Outer finally running  
```  
  
## Требования  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
> [!NOTE]
>  Начиная с Internet Explorer 8 \(стандартный режим\), блок **catch** для выполнения `finally` не требуется.  
  
## См. также  
 [Оператор throw](../../javascript/reference/throw-statement-javascript.md)   
 [Приложение\-пример мастера настройки Sсript Junkie](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)