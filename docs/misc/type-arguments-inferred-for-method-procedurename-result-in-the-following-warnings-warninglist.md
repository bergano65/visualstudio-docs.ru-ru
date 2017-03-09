---
title: "Аргументы типов, выведенные для метода &quot;&lt;procedurename&gt;&quot;, выдают следующие предупреждения: &lt;warninglist&gt; | Microsoft Docs"
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
  - "bc41006"
  - "vbc41006"
helpviewer_keywords: 
  - "BC41006"
ms.assetid: c789ffa9-0273-47f6-8915-78fc6a7d3d6d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Аргументы типов, выведенные для метода &quot;&lt;procedurename&gt;&quot;, выдают следующие предупреждения: &lt;warninglist&gt;
Универсальная процедура вызывается без указания каких\-либо аргументов типов, а выведенные аргументы типов приводят к одному или нескольким предупреждениям.  
  
 Как правило, при вызове универсального типа указывается аргумент типа для каждого параметра типа, определяемого этим универсальным типом. Если никакие аргументы типов не передаются, компилятор пытается определить типы, которые должны быть переданы параметрам типов. Если наследуемые типы вызывают неоднозначность или создают ситуацию, которая может привести к непредвиденным результатам, компилятор создает это предупреждение.  
  
 *Ограничение* для параметра типа ограничивает аргументы типов, которые могут быть переданы в него. Например, параметр типа может быть ограничен классом, который реализует интерфейс <xref:System.IComparable%601>. Дополнительные сведения см. в подразделе "Ограничения" раздела [Универсальные процедуры в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures).  
  
 По умолчанию данное сообщение является предупреждением. Сведения о скрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC41006  
  
### Исправление ошибки  
  
-   Укажите аргументы типов для универсальной процедуры, чтобы компилятору не приходилось их определять.  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Универсальные процедуры в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Список типов](/dotnet/visual-basic/language-reference/statements/type-list)