---
title: "Оператор Option Strict On не разрешает позднее связывание | Microsoft Docs"
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
  - "bc30574"
  - "vbc30574"
helpviewer_keywords: 
  - "BC30574"
ms.assetid: 9da4b826-2e12-4a5d-9e17-762b0b68fc9b
caps.latest.revision: 11
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператор Option Strict On не разрешает позднее связывание
[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] разрешает неявные преобразования между любыми типами данных. Однако может произойти потеря данных, если значение одного типа преобразуется в тип данных с меньшей точностью или меньшей емкостью.`Option Strict On` обеспечивает уведомление во время компиляции об этих типах преобразования, поэтому их можно избежать. Нельзя использовать `Option Strict On` с поздним связыванием.  
  
 В приведенном ниже коде используется позднее связывание и возникает эта ошибка, когда `Option Strict` присваивается значение `On`.  
  
 [!CODE [VbVbalrOptionStrictError#1](VbVbalrOptionStrictError#1)]  
  
 **Идентификатор ошибки:** BC30574  
  
### Исправление ошибки  
  
-   Измените объявление объекта так, чтобы использовался явный тип, как показано в приведенном ниже примере.  
  
     [!CODE [VbVbalrOptionStrictError#2](VbVbalrOptionStrictError#2)]  
  
 \-или\-  
  
-   Измените выражение позднего связывания, указав явный тип, как показано в приведенном ниже примере.  
  
     [!CODE [VbVbalrOptionStrictError#3](VbVbalrOptionStrictError#3)]  
  
 \-или\-  
  
-   Позвольте компилятору определить тип, как показано в приведенном ниже примере.  
  
     [!CODE [VbVbalrOptionStrictError#4](VbVbalrOptionStrictError#4)]  
  
 \-или\-  
  
-   Отключите `Option Strict`, удалив слово `On` после него или явно указав `Off`.  
  
## См. также  
 [Функции преобразования типов](/dotnet/visual-basic/language-reference/functions/type-conversion-functions)   
 [Оператор Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Расширяющие и сужающие преобразования](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)