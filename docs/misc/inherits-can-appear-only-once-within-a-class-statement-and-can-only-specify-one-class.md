---
title: "В операторе &quot;Class&quot; ключевое слово &quot;Inherits&quot; может использоваться только один раз и задавать только один класс. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30121"
  - "bc30121"
helpviewer_keywords: 
  - "BC30121"
ms.assetid: 4ac5b018-5632-4661-8ac6-dbda2f8c4dfe
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# В операторе &quot;Class&quot; ключевое слово &quot;Inherits&quot; может использоваться только один раз и задавать только один класс.
Несколько операторов `Inherits` находится в одном классе, или оператор `Inherits` задает более одного класса. Класс может наследовать только от одного базового класса.  
  
 **Идентификатор ошибки:** BC30121  
  
### Исправление ошибки  
  
-   Удалите все лишние операторы `Inherits` и убедитесь, что оставшийся оператор `Inherits` указывает только один базовый класс.  
  
## См. также  
 [Инструкция Inherits](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Основы наследования](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)