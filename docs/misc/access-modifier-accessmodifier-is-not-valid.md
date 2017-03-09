---
title: "Недопустимый модификатор &quot;&lt;модификатор_доступа&gt;&quot; | Microsoft Docs"
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
  - "bc31100"
  - "vbc31100"
helpviewer_keywords: 
  - "BC31100"
ms.assetid: 1cd71acc-0b54-4f64-8d61-75b272d293cb
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Недопустимый модификатор &quot;&lt;модификатор_доступа&gt;&quot;
Инструкция [Оператор Get](/dotnet/visual-basic/language-reference/statements/get-statement) или [Оператор Set](/dotnet/visual-basic/language-reference/statements/set-statement) задает уровень доступа, который является менее строгим, чем указанный для содержащего свойства.  
  
 Вы всегда можете указать уровень доступа для этого свойства. Кроме того, можно указать другой уровень доступа не более чем для одной процедуры свойства \(`Get` или `Set`\), если этот уровень является более строгим, чем базовый уровень доступа свойства. Например, если свойство — `Friend`, для процедуры свойства можно указать `Private`, но не `Public`. Нельзя задать уровни доступа для обеих процедур свойства.  
  
 **Идентификатор ошибки:** BC31100  
  
### Исправление ошибки  
  
-   Сделайте уровень доступа для процедуры свойства более строгим, чем для свойства, или полностью удалите модификатор доступа.  
  
-   Объявите менее строгий доступ уровня в [Оператор Property](/dotnet/visual-basic/language-reference/statements/property-statement) и объявите более строгий уровень доступа в одной из процедур свойства.  
  
## См. также  
 [Процедуры свойств](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Практическое руководство. Объявление свойства со смешанным уровнем доступа](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)