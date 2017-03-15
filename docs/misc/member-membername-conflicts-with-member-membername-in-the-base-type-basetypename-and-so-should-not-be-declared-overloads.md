---
title: "Член &quot;&lt;имя_члена&gt;&quot; конфликтует с членом &quot;&lt;имя_члена&gt;&quot; в базовом типе &quot;&lt;имя_базового_типа&gt;&quot;, и поэтому не должен объявляться с модификатором Overloads | Microsoft Docs"
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
  - "bc40021"
  - "vbc40021"
helpviewer_keywords: 
  - "BC40021"
ms.assetid: 2ec72726-ab0e-4545-9c1e-2409eb54482e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Член &quot;&lt;имя_члена&gt;&quot; конфликтует с членом &quot;&lt;имя_члена&gt;&quot; в базовом типе &quot;&lt;имя_базового_типа&gt;&quot;, и поэтому не должен объявляться с модификатором Overloads
Свойство или процедура использует ключевое слово [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads) для повторного объявления существующего свойства или процедуры с тем же именем, но существующее свойство или процедура находится в базовом классе.  
  
 Перегрузка используется для задания нескольких версий свойства или процедуры в одном и том же классе. Нельзя определить дополнительную версию члена базового класса, если он еще не задает [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads).  
  
 По умолчанию данное сообщение является предупреждением. Дополнительные сведения о скрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC40021  
  
### Исправление ошибки  
  
-   Если вы собираетесь определить дополнительную версию члена базового класса и имеете доступ к исходному коду базового класса, добавьте ключевое слово [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads) в определение базового класса.  
  
-   Если у вас нет доступа к исходному коду базового класса, невозможно перегрузить член в производном классе. Удалите ключевое слово `Overloads`.  
  
-   Если требуется заменить член базового класса, а не определить его дополнительную версию, используйте ключевое слово [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides) вместо `Overloads`.  
  
-   Если вы хотите, чтобы член базового класса был скрыт новым членом в производном классе, используйте ключевое слово [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows) вместо `Overloads`.  
  
## См. также  
 [Перегрузка процедур](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Основы наследования](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)