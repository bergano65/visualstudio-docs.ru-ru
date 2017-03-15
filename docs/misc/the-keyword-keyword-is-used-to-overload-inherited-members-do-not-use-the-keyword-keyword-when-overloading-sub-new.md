---
title: "Ключевое слово &quot;&lt;ключевое_слово&gt;&quot; используется для перегрузки наследуемых членов. Не используйте ключевое слово &quot;&lt;ключевое_слово&gt;&quot; при перегрузке &quot;Sub New&quot; | Microsoft Docs"
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
  - "vbc32040"
  - "bc32040"
helpviewer_keywords: 
  - "BC32040"
ms.assetid: 39e6ee0d-b8a0-498e-bdaf-a4ceb13892fe
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ключевое слово &quot;&lt;ключевое_слово&gt;&quot; используется для перегрузки наследуемых членов. Не используйте ключевое слово &quot;&lt;ключевое_слово&gt;&quot; при перегрузке &quot;Sub New&quot;
Конструктор объявлен с ключевым словом `Overloads`.  
  
 Visual Basic не поддерживает наследование или перегрузку конструкторов.  
  
 **Идентификатор ошибки:** BC32040  
  
### Исправление ошибки  
  
-   Удалите ключевое слово `Overloads` из всех объявлений конструктора.  
  
## См. также  
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [НЕ В СБОРКЕ. Использование конструкторов и деструкторов](http://msdn.microsoft.com/ru-ru/548eebe1-86c4-4377-b2f5-447cb8be3d90)