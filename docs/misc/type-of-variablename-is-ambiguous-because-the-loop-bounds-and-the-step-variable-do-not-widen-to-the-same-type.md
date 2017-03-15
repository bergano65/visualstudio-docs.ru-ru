---
title: "Тип &quot;&lt;имя_переменной&gt;&quot; является неоднозначным, так как для границ цикла и переменной шага нет расширяющего преобразования к одному типу | Microsoft Docs"
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
  - "vbc30983"
  - "bc30983"
helpviewer_keywords: 
  - "BC30983"
ms.assetid: 6b97153c-dee3-4429-b92a-2e5a212c864b
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Тип &quot;&lt;имя_переменной&gt;&quot; является неоднозначным, так как для границ цикла и переменной шага нет расширяющего преобразования к одному типу
Код содержит цикл `For...Next`, в котором компилятор не может вывести тип данных для управляющей переменной цикла, так как выполняются указанные ниже условия.  
  
-   Тип данных управляющей переменной цикла не указан с помощью выражения `As`.  
  
-   Границы цикла и переменная шага содержат по крайней мере два типа данных.  
  
-   Между типами данных возможно несколько преобразований.  
  
-   Среди кандидатов нет лучшего типа, поэтому выбор типа для управляющей переменной цикла неоднозначен.  
  
 Например, приведенный ниже цикл имеет одну границу цикла типа `Integer` и одну границу типа `UInteger`.  
  
```vb#  
Dim m As Integer = 1 Dim n As UInteger = 10 ' Not valid. ' For i = m To n ' Loop processing. ' Next  
```  
  
 Возможны преобразования между `Integer` и `UInteger` и между `UInteger` и `Integer`, но оба преобразования сужающие, поэтому ни одно из них не является лучшим.  
  
 В следующем примере добавляется третья переменная типа `Double`. Как `Integer`, так и `UInteger` имеют стандартные расширяющие преобразования в `Double`, вследствие чего преобразование в `Double` является лучшим вариантом. В результате вывода типа управляющей переменной цикла `i` присваивается тип данных `Double`.  
  
```vb#  
Dim stepVar As Double = 1 ' Valid. For i = m To n Step stepVar ' Loop processing. Next  
```  
  
 **Идентификатор ошибки:** BC30983  
  
### Исправление ошибки  
  
-   Явным образом преобразуйте одну из переменных в тип, для которого у остальных есть расширяющие преобразования, например:  
  
    ```  
    For i = m To CLng(n)  
    ```  
  
-   Используйте выражение `As`, чтобы указать тип управляющей переменной:  
  
    ```  
    For i As Double = m To n   
    ```  
  
## См. также  
 [Оператор For...Next](/dotnet/visual-basic/language-reference/statements/for-next-statement)   
 [Явные и неявные преобразования](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)   
 [Вывод локального типа](/dotnet/visual-basic/programming-guide/language-features/variables/local-type-inference)   
 [Option Infer \- оператор](/dotnet/visual-basic/language-reference/statements/option-infer-statement)   
 [Расширяющие и сужающие преобразования](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)