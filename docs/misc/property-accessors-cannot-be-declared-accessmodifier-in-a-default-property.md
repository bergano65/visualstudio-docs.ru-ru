---
title: "Методы доступа к свойствам нельзя объявлять как &quot;&lt;модификатор_доступа&gt;&quot; в свойстве со спецификатором Default. | Microsoft Docs"
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
  - "bc31107"
  - "vbc31107"
helpviewer_keywords: 
  - "BC31107"
ms.assetid: 25657b33-df85-4535-8043-69795c987175
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Методы доступа к свойствам нельзя объявлять как &quot;&lt;модификатор_доступа&gt;&quot; в свойстве со спецификатором Default.
Оператор [Оператор Get](/dotnet/visual-basic/language-reference/statements/get-statement) или [Оператор Set](/dotnet/visual-basic/language-reference/statements/set-statement) в свойстве по умолчанию включает ключевое слово `Private`.  
  
 Свойство по умолчанию не может быть `Private`, как и не могут его отдельные процедуры свойств \(`Get` или `Set`\).  
  
 **Идентификатор ошибки:** BC31107  
  
### Исправление ошибки  
  
-   Удалите ключевое слово `Private` из оператора `Get` или `Set` или удалите `Default` из [Оператор Property](/dotnet/visual-basic/language-reference/statements/property-statement).  
  
## См. также  
 [Процедуры свойств](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Практическое руководство. Объявление свойства со смешанным уровнем доступа](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)   
 [Практическое руководство. Объявление и вызов свойства по умолчанию в Visual Basic](../Topic/How%20to:%20Declare%20and%20Call%20a%20Default%20Property%20in%20Visual%20Basic.md)