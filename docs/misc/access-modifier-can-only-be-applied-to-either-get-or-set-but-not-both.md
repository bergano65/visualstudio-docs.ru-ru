---
title: "Модификатор доступа может применяться либо к Get, либо к Set, но не к обоим операторам | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31101"
  - "vbc31101"
helpviewer_keywords: 
  - "BC31101"
ms.assetid: c2a0580c-ff2f-4cc9-9113-6e540f906eec
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Модификатор доступа может применяться либо к Get, либо к Set, но не к обоим операторам
Объявление свойства задает уровень доступа в [Оператор Property](/dotnet/visual-basic/language-reference/statements/property-statement), [Оператор Get](/dotnet/visual-basic/language-reference/statements/get-statement) и [Оператор Set](/dotnet/visual-basic/language-reference/statements/set-statement).  
  
 Вы всегда можете указать уровень доступа для этого свойства. Кроме того, можно указать другой уровень доступа не более чем для одной процедуры свойства \(`Get` или `Set`\), если этот уровень является более строгим, чем базовый уровень доступа свойства. Нельзя задать уровни доступа для обеих процедур свойства.  
  
 **Идентификатор ошибки:** BC31101  
  
### Исправление ошибки  
  
-   Удалите модификатор доступа из оператора `Get` или из оператора `Set`.  
  
## См. также  
 [Процедуры свойств](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Практическое руководство. Объявление свойства со смешанным уровнем доступа](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)