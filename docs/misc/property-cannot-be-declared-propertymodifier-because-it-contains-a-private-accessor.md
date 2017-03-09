---
title: "Свойство не может быть объявлено как &quot;&lt;модификатор_свойства&gt;&quot;, поскольку оно содержит метод доступа Private | Microsoft Docs"
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
  - "vbc31108"
  - "bc31108"
helpviewer_keywords: 
  - "BC31108"
ms.assetid: 74fb36f4-54cd-4fda-bcc6-e965b5c7c37b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Свойство не может быть объявлено как &quot;&lt;модификатор_свойства&gt;&quot;, поскольку оно содержит метод доступа Private
Свойство с процедурой `Private` \(`Get` или `Set`\) помечено как [Overridable](/dotnet/visual-basic/language-reference/modifiers/overridable).  
  
 Если свойство или процедура базового класса объявлены как [Private](/dotnet/visual-basic/language-reference/modifiers/private), производный класс не может переопределять это свойство или процедуру, так как он не может получить к ним доступ. Таким образом, нельзя использовать `Private` в сочетании с `Overridable`. Это относится не только к самому свойству, но и к отдельным его процедурам.  
  
 **Идентификатор ошибки:** BC31108  
  
### Исправление ошибки  
  
-   Удалите ключевое слово `Overridable` из [Оператор Property](/dotnet/visual-basic/language-reference/statements/property-statement) либо удалите ключевое слово `Private` из [Оператор Get](/dotnet/visual-basic/language-reference/statements/get-statement) или [Оператор Set](/dotnet/visual-basic/language-reference/statements/set-statement).  
  
## См. также  
 [Процедуры свойств](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Практическое руководство. Объявление свойства со смешанным уровнем доступа](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)