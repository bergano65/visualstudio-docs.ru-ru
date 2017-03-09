---
title: "Не удается определить общий тип второго и третьего операнда оператора &quot;If&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc33106"
  - "bc33106"
helpviewer_keywords: 
  - "BC33106"
ms.assetid: 793eed88-a9f9-43e3-b657-c16795ecbbcc
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Не удается определить общий тип второго и третьего операнда оператора &quot;If&quot;
Не удается определить общий тип второго и третьего операнда оператора "If". Один из них должен иметь расширяющее преобразование в другой.  
  
 Если оператор `If` вызывается с тремя аргументами, необходимо выполнить расширяющее преобразование для второго и третьего аргументов. Например, из\-за отсутствия расширяющего преобразования в любом направлении между `Integer` и `String` приведенный ниже код вызывает эту ошибку.  
  
```vb#  
Dim divisor = 3  
' Not valid.  
' Console.WriteLine(If(divisor <> 0, number \ divisor, "Division by zero"))  
```  
  
 **Идентификатор ошибки:** BC33106  
  
### Исправление ошибки  
  
-   Выполните явное преобразование одного из операндов в коде, если это возможно.  
  
-   Используйте другую условную конструкцию, например оператор `If...Then...Else`.  
  
## См. также  
 [Оператор If](/dotnet/visual-basic/language-reference/operators/if-operator)   
 [Оператор If...Then...Else](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)   
 [Расширяющие и сужающие преобразования](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)