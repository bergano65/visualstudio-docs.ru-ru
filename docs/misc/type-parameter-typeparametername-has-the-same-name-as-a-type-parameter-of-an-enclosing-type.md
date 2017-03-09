---
title: "Параметр типа &quot;&lt;имя_параметра_типа&gt;&quot; имеет то же имя, что и параметр типа, в который он входит | Microsoft Docs"
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
  - "vbc40048"
  - "bc40048"
helpviewer_keywords: 
  - "BC40048"
ms.assetid: d5428b36-88d3-42c4-a096-cbc7bb9571f2
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Параметр типа &quot;&lt;имя_параметра_типа&gt;&quot; имеет то же имя, что и параметр типа, в который он входит
Параметр универсального типа объявлен с таким же именем, что и у параметра типа содержащего универсального типа.  
  
 В списке параметров универсального типа каждый параметр должен иметь имя, не совпадающее ни с одним из следующих имен:  
  
-   с именем каждого из других параметров типов в том же списке параметров типов;  
  
-   с именем параметра из списка параметров типов любого имеющегося универсального типа;  
  
-   с именем самого универсального типа.  
  
 По умолчанию данное сообщение является предупреждением. Сведения о скрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC40048  
  
### Исправление ошибки  
  
-   Переименуйте параметр типа, чтобы он отличался от всех имен, указанных на этой странице справки.  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Список типов](/dotnet/visual-basic/language-reference/statements/type-list)