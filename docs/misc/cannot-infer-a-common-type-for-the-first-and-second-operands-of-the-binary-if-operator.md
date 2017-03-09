---
title: "Не удается определить общий тип первого и второго операндов бинарного оператора If | Microsoft Docs"
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
  - "vbc33110"
  - "bc33110"
helpviewer_keywords: 
  - "BC33110"
ms.assetid: f46873aa-f6cd-4cc9-9e8e-e668bddf0980
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Не удается определить общий тип первого и второго операндов бинарного оператора If
Не удается определить общий тип первого и второго операндов бинарного оператора If. Один из них должен иметь расширяющее преобразование в другой.  
  
 Бинарный оператор `If` требует наличия расширяющего преобразования между одним из аргументов и другим аргументом. Например, из\-за отсутствия расширяющего преобразования в любом направлении между `Integer` и `String` приведенный ниже код вызывает эту ошибку.  
  
```vb#  
Dim first? As Integer  
Dim second As String = "First is Nothing"  
'' Not valid.  
' Console.WriteLine(If(first, second))  
```  
  
 **Идентификатор ошибки:** BC33110  
  
### Исправление ошибки  
  
-   Предоставьте явное преобразование для одного из операндов в коде, если это возможно.  
  
    ```  
    Console.WriteLine(If(first, CInt(second)))   
    ```  
  
-   Перепишите код, используя другую условную конструкцию.  
  
    ```  
    If first IsNot Nothing Then  
        Console.WriteLine(first)  
    Else  
        Console.WriteLine(second)  
    End If  
    ```  
  
## См. также  
 [Оператор If](/dotnet/visual-basic/language-reference/operators/if-operator)   
 [Расширяющие и сужающие преобразования](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [Оператор If...Then...Else](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)