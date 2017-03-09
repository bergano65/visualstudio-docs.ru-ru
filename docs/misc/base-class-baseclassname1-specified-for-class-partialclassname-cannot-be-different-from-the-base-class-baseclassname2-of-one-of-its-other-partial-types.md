---
title: "Базовый класс &quot;&lt;имя_базового_класса1&gt;&quot;, указанный для класса &quot;&lt;имя_разделяемого_класса&gt;&quot; не может отличаться от базового класса &quot;&lt;имя_базового_класса2&gt;&quot; одного из его других разделяемых типов | Microsoft Docs"
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
  - "BC30928"
  - "vbc30928"
helpviewer_keywords: 
  - "BC30928"
ms.assetid: da464f09-1016-4dec-beb7-3202cacd8e1e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Базовый класс &quot;&lt;имя_базового_класса1&gt;&quot;, указанный для класса &quot;&lt;имя_разделяемого_класса&gt;&quot; не может отличаться от базового класса &quot;&lt;имя_базового_класса2&gt;&quot; одного из его других разделяемых типов
Класс задается в двух или более частичных объявлениях, которые содержат несколько [Инструкция Inherits](/dotnet/visual-basic/language-reference/statements/inherits-statement), указывающих несколько базовых классов.  
  
 При разделении определения класса на несколько частичных объявлений компилятор обрабатывает класс как объединение всех его частичных объявлений. Это относится не только к членам, но также и к реализации, наследованию и уровню доступа.  
  
 Класс может реализовывать несколько интерфейсов, но не может наследовать от нескольких базовых классов. Таким образом, все инструкции `Inherits` должны указывать один и тот же базовый класс.  
  
 **Идентификатор ошибки:** BC30928  
  
### Исправление ошибки  
  
-   Решите, какой класс должен быть базовым классом вашего разделяемого класса, и удалите из его частичных объявлений все инструкции `Inherits`, указывающие другой базовый класс.  
  
## См. также  
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [Инструкция Inherits](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Основы наследования](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)