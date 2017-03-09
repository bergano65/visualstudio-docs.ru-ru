---
title: "Оператор Return в Sub и Set не может возвращать значение | Microsoft Docs"
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
  - "bc30647"
  - "vbc30647"
helpviewer_keywords: 
  - "BC30647"
ms.assetid: d4c05c28-d650-4f49-976e-650d84802036
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператор Return в Sub и Set не может возвращать значение
Процедуры `Sub` и процедуры свойств `Set` не могут возвращать значения.  
  
 **Идентификатор ошибки:** BC30647  
  
### Исправление ошибки  
  
-   Преобразуйте текущую процедуру в функцию или в процедуру свойства `Get`, если эта процедура является частью свойства.  
  
-   Эффективный возврат значений из процедур `Sub` возможен путем изменения значений параметров, переданных по ссылке с помощью ключевого слова `ByRef`.  
  
## См. также  
 [Оператор Return](/dotnet/visual-basic/language-reference/statements/return-statement)   
 [Подпрограммы](/dotnet/visual-basic/programming-guide/language-features/procedures/sub-procedures)   
 [Процедуры Function](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)   
 [Процедуры свойств](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)