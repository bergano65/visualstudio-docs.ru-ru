---
title: "Тип &quot;&lt;имя_типа&gt;&quot; и разделяемый тип &quot;&lt;имя_типа&gt;&quot; конфликтуют в контейнере &quot;&lt;имя_контейнера&gt;&quot;, но выполняется их объединение, так как один из них объявлен разделяемым. | Microsoft Docs"
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
  - "bc40046"
  - "vbc40046"
helpviewer_keywords: 
  - "BC40046"
ms.assetid: c243e70b-ecd5-49ef-a260-a7bb12a4a3b1
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Тип &quot;&lt;имя_типа&gt;&quot; и разделяемый тип &quot;&lt;имя_типа&gt;&quot; конфликтуют в контейнере &quot;&lt;имя_контейнера&gt;&quot;, но выполняется их объединение, так как один из них объявлен разделяемым.
Класс или структура присутствует в нескольких определениях в одном типе контейнера, и атрибутом `Partial` не помечено не менее двух определений.  
  
 Вы должны использовать ключевое слово [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) по крайней мере в одном из нескольких определений класса или структуры, но рекомендуется использовать его во всех разделяемых определениях.  
  
 По умолчанию данное сообщение является предупреждением. Сведения о скрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC40046  
  
### Исправление ошибки  
  
-   Используйте ключевое слово [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) в каждом частичном определении класса или структуры.  
  
## См. также  
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)