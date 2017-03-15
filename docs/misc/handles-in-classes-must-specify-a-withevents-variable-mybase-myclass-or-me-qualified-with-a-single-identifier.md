---
title: "&quot;Handles&quot; в классах должны задавать переменную &quot;WithEvents&quot;, &quot;MyBase&quot;, &quot;MyClass&quot; или &quot;Me&quot;, определенную с одним идентификатором. | Microsoft Docs"
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
  - "bc31412"
  - "vbc31412"
helpviewer_keywords: 
  - "BC31412"
ms.assetid: acbefc38-448a-4afa-90c2-77389415d618
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Handles&quot; в классах должны задавать переменную &quot;WithEvents&quot;, &quot;MyBase&quot;, &quot;MyClass&quot; или &quot;Me&quot;, определенную с одним идентификатором.
Чтобы задать обработчик событий, операторы `Handles` должны указывать либо объектную переменную, объявленную с ключевым словом `WithEvents`, либо член, дополненный ключевым словом `MyBase`.  
  
 **Идентификатор ошибки:** BC31412  
  
### Исправление ошибки  
  
1.  Используйте модификатор `WithEvents` для объявления переменных, которые будут использоваться с оператором `Handles`.  
  
2.  Укажите имя события для текущего класса в базовом классе.  
  
## См. также  
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [WithEvents](/dotnet/visual-basic/language-reference/modifiers/withevents)   
 [События](/dotnet/visual-basic/programming-guide/language-features/events/events)