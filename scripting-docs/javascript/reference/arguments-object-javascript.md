---
title: "Объект arguments (JavaScript) | Microsoft Docs"
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
  - "arguments"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "arguments - объект"
  - "аргументы, arguments - объект"
ms.assetid: 5eb79ca9-bbb8-4a42-aaf5-16a93ecb425f
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Объект arguments (JavaScript)
Объект, представляющий аргументы для выполняемых в данный момент функций и функции, вызвавшие его.  
  
## Синтаксис  
  
```  
[function.]arguments[n]  
```  
  
## Параметры  
 *function*  
 Необязательный параметр.  Имя объекта `Function`, выполняемого в данный момент.  
  
 *n*  
 Обязательный параметр.  Начинающийся с нуля индекс значений аргумента, передаваемых в объект `Function`.  
  
## Заметки  
 Нельзя явно создать объект **arguments**.  Объект **arguments** становится доступным только когда функция начинает выполняться.  Объект **arguments** функции не является массивом, однако доступ к отдельным аргументам осуществляется тем же способом, каким обращаются к элементам массива.  Индекс *n* фактически является ссылкой на одно из свойств **0** ***n*** объекта **arguments**.  
  
## Пример  
 В следующем примере показано, как используется объект **arguments**.  
  
```javascript  
function ArgTest(a, b)  
{  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
   s += "<br />";  
  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++)  
   {  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
  
   document.write(s);  
}  
  
ArgTest(1, 2, "hello", new Date())  
  
// Output:  
// Expected Arguments: 2  
// Passed Arguments: 4  
// The individual arguments are: 1 2 hello Tues Jan 8 08:27:09 PST 20xx  
  
```  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Свойства 0...n \(arguments\)](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md)   
 [Свойство callee \(arguments\)](../../javascript/reference/callee-property-arguments-javascript.md)   
 [Свойство length \(arguments\)](../../javascript/reference/length-property-arguments-javascript.md)