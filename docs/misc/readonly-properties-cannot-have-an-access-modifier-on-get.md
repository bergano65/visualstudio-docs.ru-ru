---
title: "Свойства &quot;ReadOnly&quot; не могут иметь модификатор доступа в &quot;Get&quot; | Microsoft Docs"
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
  - "vbc31105"
  - "bc31105"
helpviewer_keywords: 
  - "BC31105"
ms.assetid: 54066d8e-eb22-4b99-bb18-45afe61d3b33
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Свойства &quot;ReadOnly&quot; не могут иметь модификатор доступа в &quot;Get&quot;
Объявление свойства `ReadOnly` задает уровни доступа в [Оператор Property](/dotnet/visual-basic/language-reference/statements/property-statement) и [Оператор Get](/dotnet/visual-basic/language-reference/statements/get-statement).  
  
 Вы всегда можете указать уровень доступа для свойства. Кроме того, можно указать другой уровень доступа не более чем для одной процедуры свойства \(`Get` или `Set`\), если этот уровень является более строгим, чем базовый уровень доступа свойства. Нельзя задать уровни доступа для обеих процедур свойства.  
  
 **Идентификатор ошибки:** BC31105  
  
### Исправление ошибки  
  
-   Удалите модификатор доступа из оператора `Get`. Он представляет все свойство `ReadOnly` целиком, а два уровня доступа для свойства быть не должно.  
  
## См. также  
 [Процедуры свойств](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Практическое руководство. Объявление свойства со смешанным уровнем доступа](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)