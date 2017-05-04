---
title: "Свойство arguments (Function) (JavaScript) | Microsoft Docs"
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
  - "аргументы, свойство arguments"
  - "Arguments - свойство"
ms.assetid: efc7a1ee-0880-4f05-b0f2-808f31a4af1d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Свойство arguments (Function) (JavaScript)
Получает аргументы выполняемого в данный момент объекта `Function`.  
  
## Синтаксис  
  
```  
  
function.arguments  
```  
  
## Заметки  
 Аргумент `function` — это имя выполняемой в данный момент функции, и он может быть пропущен.  
  
 Это свойство позволяет функции обрабатывать различное число аргументов.  Свойство **length** объекта `arguments` содержит число аргументов, переданных функции.  Отдельные аргументы, содержащиеся в объекте `arguments`, доступны таким же образом, как элементы массива.  
  
## Пример  
 В следующем примере показано использование свойства `arguments`.  
  
```javascript  
function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
//Output: function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
// Output: The individual arguments are: 1 2 hello  
```  
  
## Требования  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## См. также  
 [Объект arguments](../../javascript/reference/arguments-object-javascript.md)   
 [Оператор function](../../javascript/reference/function-statement-javascript.md)