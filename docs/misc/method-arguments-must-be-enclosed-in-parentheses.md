---
title: "Аргументы метода должны быть заключены в круглые скобки | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30800"
  - "bc30800"
helpviewer_keywords: 
  - "BC30800"
ms.assetid: ecdec760-8b51-474f-acad-17cf8059d83b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Аргументы метода должны быть заключены в круглые скобки
Правила, управляющие вызовами процедур, стали проще в более новых версиях [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Все аргументы должны быть заключены в круглые скобки.  
  
 **Идентификатор ошибки:** BC30800  
  
### Исправление ошибки  
  
-   Заключите список аргументов в скобки; например:  
  
    ```  
    MySub(ArrayIndex, NewValue)  
    ```  
  
## См. также  
 [Procedure Calling Sequence Changes in Visual Basic](http://msdn.microsoft.com/ru-ru/4ef1eea6-36cb-4b97-a31b-9ba65e46a9fd)   
 [Параметры и аргументы процедуры](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments)