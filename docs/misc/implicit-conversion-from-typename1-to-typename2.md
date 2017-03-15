---
title: "Неявное преобразование из &quot;&lt;имя_типа1&gt;&quot; в &quot;&lt;имя_типа2&gt;&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42016"
  - "BC42016"
helpviewer_keywords: 
  - "BC42016"
ms.assetid: 7dabaab0-8258-4c17-927f-28e61f50bd3a
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Неявное преобразование из &quot;&lt;имя_типа1&gt;&quot; в &quot;&lt;имя_типа2&gt;&quot;
Выражение или оператор присваивания получает значение одного типа данных и преобразует его в другой тип. Так как ключевые слова преобразования не используются, преобразование является *неявным*.  
  
 По умолчанию данное сообщение является предупреждением. Сведения о скрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC42016  
  
### Исправление ошибки  
  
-   По возможности используйте значения одного типа данных, чтобы среде [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] не нужно было выполнять никаких преобразований.  
  
-   Используйте `CType` или другое ключевое слово преобразования, чтобы преобразование было *явным*.  
  
## См. также  
 [Явные и неявные преобразования](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)   
 [Функции преобразования типов](/dotnet/visual-basic/language-reference/functions/type-conversion-functions)