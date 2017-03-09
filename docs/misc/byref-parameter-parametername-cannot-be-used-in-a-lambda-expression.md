---
title: "Параметр ByRef &quot;&lt;имя_параметра&gt;&quot; нельзя использовать в лямбда-выражении | Microsoft Docs"
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
  - "bc36639"
  - "vbc36639"
helpviewer_keywords: 
  - "BC36639"
ms.assetid: 5913f9b6-2929-4c05-8dd1-00b10fcd5a83
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Параметр ByRef &quot;&lt;имя_параметра&gt;&quot; нельзя использовать в лямбда-выражении
Лямбда\-выражение, объявленное в `Sub` или функции, не может использовать любые параметры `ByRef` этого `Sub` или функции. Например, следующий код вызовет эту ошибку, поскольку параметр `ByRef``n` используется в лямбда\-выражении.  
  
```  
'' Not valid.   
'Sub ExampleSub(ByRef n As Integer)  
  
'    Dim lambda = Function(p As Integer) p + n  
  
'End Sub  
```  
  
 **Идентификатор ошибки:** BC36639  
  
### Исправление ошибки  
  
-   Назначьте параметр `ByRef` локальной переменной и используйте эту локальную переменную в лямбда\-выражении, как показано в следующем коде.  
  
    ```  
    Sub ExampleSub(ByRef n As Integer)  
  
        Dim temp = n  
        Dim lambda = Function(p As Integer) p + temp  
  
    End Sub  
    ```  
  
## См. также  
 [Лямбда\-выражения](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)