---
title: "Использование оператора Exit Sub в функциях и свойствах недопустимо | Microsoft Docs"
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
  - "bc30065"
  - "vbc30065"
helpviewer_keywords: 
  - "BC30065"
ms.assetid: d6426861-ba64-4dca-9100-262c6c058bd9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Использование оператора Exit Sub в функциях и свойствах недопустимо
`Exit Sub` используется в процедуре `Function` или процедуре `Property`. Оператор `Exit` должен соответствовать блоку, в котором он используется.  
  
 **Идентификатор ошибки:** BC30065  
  
### Исправление ошибки  
  
-   Замените `Exit Sub` на оператор `Exit Function` или `Exit Property`.  
  
## См. также  
 [Подпрограммы](/dotnet/visual-basic/programming-guide/language-features/procedures/sub-procedures)   
 [Процедуры Function](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)   
 [Процедуры свойств](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)