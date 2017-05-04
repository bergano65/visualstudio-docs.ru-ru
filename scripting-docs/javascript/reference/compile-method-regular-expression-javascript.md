---
title: "Метод compile (Regular Expression) (JavaScript) | Microsoft Docs"
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
  - "compile"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Compile - метод"
  - "компиляция исходного кода, регулярные выражения"
  - "регулярные выражения, компиляция"
ms.assetid: dc28cae3-478d-49b5-b5ea-203e5edfe195
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Метод compile (Regular Expression) (JavaScript)
Выполняет компиляцию регулярного выражения во внутренний формат для более быстрого выполнения.  
  
## Синтаксис  
  
```  
  
rgExp.compile(pattern, [flags])   
```  
  
## Параметры  
 `rgExp`  
 Обязательный.  Экземпляр объекта **Regular Expression**.  Может быть именем переменной или литералом.  
  
 *pattern*  
 Обязательный.  Строковое выражение, содержащее шаблон регулярного выражения для компиляции.  
  
 `flags`  
 Необязательный.  Далее перечислены доступные флаги, которые можно сочетать.  
  
-   g \(глобальный поиск всех вхождений шаблона *pattern*\)  
  
-   i \(не учитывать регистр\)  
  
-   m \(многостроковый поиск\)  
  
## Заметки  
 Метод **compile** преобразует выражение *pattern* во внутренний формат для более быстрого выполнения.  Это позволяет, например, более эффективно использовать регулярные выражения в циклах.  Благодаря компиляции регулярного выражения ускоряется выполнение программы при неоднократном повторном использовании одного и того же регулярного выражения.  Если регулярное выражение меняется, то его компиляция не предоставляет никаких преимуществ.  
  
## Пример  
 В следующем примере показано использование метода **compile**.  
  
```javascript  
function CompileDemo(){  
   var rs;  
   var s = "AaBbCcDdEeFfGgHhIiJjKkLlMmNnOoPp"  
   // Create regular expression for uppercase only.  
   var r = new RegExp("[A-Z]", "g");  
   var a1 = s.match(r)              // Find matches.  
   // Compile the regular expression for lowercase only.  
   r.compile("[a-z]", "g");  
// Find matches.  
   var a2 = s.match(r)                
   return(a1 + "\n" + a2);  
}  
```  
  
## Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Относится к**: [Объект Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)  
  
## См. также  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ru-ru/ab0766e1-7037-45ed-aa23-706f58358c0e)