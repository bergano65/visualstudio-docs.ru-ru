---
title: "Свойства со спецификатором WriteOnly не могут иметь модификатор доступа для Set | Microsoft Docs"
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
  - "bc31104"
  - "vbc31104"
helpviewer_keywords: 
  - "BC31104"
ms.assetid: d1ac04a8-e436-4f3e-8d71-fc4569b35fcd
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Свойства со спецификатором WriteOnly не могут иметь модификатор доступа для Set
Объявление свойства `WriteOnly` задает уровень доступа в [Оператор Property](/dotnet/visual-basic/language-reference/statements/property-statement) и [Оператор Set](/dotnet/visual-basic/language-reference/statements/set-statement).  
  
 Вы всегда можете указать уровень доступа для свойства. Кроме того, можно указать другой уровень доступа не более чем для одной процедуры свойства \(`Get` или `Set`\), если этот уровень является более строгим, чем базовый уровень доступа свойства. Нельзя задать уровни доступа для обеих процедур свойства.  
  
 **Идентификатор ошибки:** BC31104  
  
### Исправление ошибки  
  
-   Удалите модификатор доступа из оператора `Set`. Он представляет все свойство `WriteOnly` целиком, а два уровня доступа для свойства быть не должно.  
  
## См. также  
 [Процедуры свойств](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Практическое руководство. Объявление свойства со смешанным уровнем доступа](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)