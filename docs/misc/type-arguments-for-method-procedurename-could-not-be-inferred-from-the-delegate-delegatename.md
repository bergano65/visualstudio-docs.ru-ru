---
title: "Аргументы типа для метода &quot;&lt;имя_процедуры&gt;&quot; не могут быть выведены от делегата &quot;&lt;имя_делегата&gt;&quot; | Microsoft Docs"
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
  - "vbc30952"
  - "bc30952"
helpviewer_keywords: 
  - "BC30952"
ms.assetid: 5eb804ce-2e93-4668-b655-7fe00815e552
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Аргументы типа для метода &quot;&lt;имя_процедуры&gt;&quot; не могут быть выведены от делегата &quot;&lt;имя_делегата&gt;&quot;
Оператор назначения использует `AddressOf` для назначения делегату адреса универсальной процедуры, но он не предоставляет универсальной процедуре никакие аргументы типа.  
  
 Как правило, при вызове универсального типа указывается аргумент типа для каждого параметра типа, определяемого этим универсальным типом. Если вы не предоставляете никакие аргументы типов, компилятор пытается вывести типы, которые должны быть переданы в параметры типов. Если контекст не предоставляет достаточно сведений, чтобы компилятор мог вывести типы, возникает ошибка.  
  
 **Идентификатор ошибки:** BC30952  
  
### Исправление ошибки  
  
-   Укажите аргументы типа для универсальной процедуры в выражении `AddressOf`.  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Оператор AddressOf](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [Универсальные процедуры в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Список типов](/dotnet/visual-basic/language-reference/statements/type-list)