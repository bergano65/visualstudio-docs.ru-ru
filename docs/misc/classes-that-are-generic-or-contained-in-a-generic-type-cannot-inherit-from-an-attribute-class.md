---
title: "Классы, которые являются общими или ограниченными в общем типе, не могут наследоваться от класса атрибута | Microsoft Docs"
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
  - "vbc32074"
  - "BC32074"
helpviewer_keywords: 
  - "BC32074"
ms.assetid: 3552ac98-d86a-4962-9d51-b9a8acc38ea1
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Классы, которые являются общими или ограниченными в общем типе, не могут наследоваться от класса атрибута
Класс, являющийся универсальным или вложенным в универсальный тип, указывает, что он наследуется от класса атрибутов.  
  
 Visual Basic и .NET Framework в настоящее время не поддерживают никаких сочетаний атрибутов и универсальных типов. Это означает, что действуют указанные ниже ограничения.  
  
-   Атрибут не может быть универсальным типом или объявляться внутри универсального типа.  
  
-   Атрибут не может наследоваться от универсального класса, а универсальный класс не может наследоваться от атрибута.  
  
-   При применении атрибута нельзя ввести аргумент, который является:  
  
    -   универсальным типом;  
  
    -   типом, построенным на основе универсального типа;  
  
    -   параметром содержащего типа;  
  
    -   типом, построенным на основе параметра содержащего типа.  
  
 **Идентификатор ошибки:** BC32074  
  
### Исправление ошибки  
  
-   Измените базовый класс на отличный от класса атрибутов или полностью удалите оператор `Inherits`.  
  
## См. также  
 <xref:System.Attribute>   
 [НЕ В СБОРКЕ. Обзор атрибутов в Visual Basic](http://msdn.microsoft.com/ru-ru/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Основы наследования](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [Инструкция Inherits](/dotnet/visual-basic/language-reference/statements/inherits-statement)