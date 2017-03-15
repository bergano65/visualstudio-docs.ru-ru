---
title: "Недопустимое использование ключевого слова &quot;&lt;ключевое_слово&gt;&quot; в модуле | Microsoft Docs"
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
  - "vbc42028"
  - "BC42028"
helpviewer_keywords: 
  - "BC42028"
ms.assetid: a9bc1e9d-ba2c-4a71-b147-0fb66f670316
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Недопустимое использование ключевого слова &quot;&lt;ключевое_слово&gt;&quot; в модуле
Модули не имеют экземпляров, не поддерживают наследование и не реализуют интерфейсы. Поэтому следующие ключевые слова не применяются к объявлению модуля:  
  
-   [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)  
  
-   [NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)  
  
-   [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)  
  
-   [Private](/dotnet/visual-basic/language-reference/modifiers/private)  
  
-   [Protected](/dotnet/visual-basic/language-reference/modifiers/protected)  
  
-   [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)  
  
-   [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)  
  
-   [Static](/dotnet/visual-basic/language-reference/modifiers/static)  
  
 Единственные ключевые слова, поддерживаемые в [Оператор Module](/dotnet/visual-basic/language-reference/statements/module-statement), — [Public](/dotnet/visual-basic/language-reference/modifiers/public) и [Friend](/dotnet/visual-basic/language-reference/modifiers/friend).  
  
 Кроме того, нельзя использовать оператор [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause) или [Инструкция Inherits](/dotnet/visual-basic/language-reference/statements/inherits-statement) в блоке операторов модуля.  
  
 По умолчанию данное сообщение является предупреждением. Дополнительные сведения о скрытии предупреждений и обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC42028  
  
### Исправление ошибки  
  
-   Если предполагается, что элемент программирования будет модулем, следует использовать только ключевое слово `Public` или `Friend` в его объявлении. По умолчанию модуль использует ключевое слово `Friend`, если не указан его уровень доступа.  
  
-   Если вы планируете создавать экземпляры этого элемента программирования, следует объявить его как класс. После этого можно использовать ключевые слова, применяемые к объявлению класса.  
  
## См. также  
 [Оператор Class](/dotnet/visual-basic/language-reference/statements/class-statement)