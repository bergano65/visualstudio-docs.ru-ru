---
title: "Указанный доступ &quot;&lt;уровень_доступа1&gt;&quot; для &quot;&lt;имя_разделяемого_типа&gt;&quot; не соответствует доступу &quot;&lt;уровень_доступа2&gt;&quot;, указанному в одном из его других разделяемых типов | Microsoft Docs"
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
  - "vbc30925"
  - "BC30925"
helpviewer_keywords: 
  - "BC30925"
ms.assetid: aabe0f4a-dc02-4828-a837-20cd47a7bd43
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Указанный доступ &quot;&lt;уровень_доступа1&gt;&quot; для &quot;&lt;имя_разделяемого_типа&gt;&quot; не соответствует доступу &quot;&lt;уровень_доступа2&gt;&quot;, указанному в одном из его других разделяемых типов
Класс или структура определена в нескольких частичных объявлениях с конфликтующими спецификациями уровня доступа.  
  
 После разделения определения класса или структуры на несколько частичных объявлений компилятор обрабатывает тип как объединение всех частичных объявлений. Это относится не только к членам, но также и к реализации, наследованию и уровню доступа.  
  
 Нельзя смешивать уровни доступа в определении класса или структуры. Даже сочетание `Protected Friend` допускается только в том случае, если ключевые слова являются смежными в одной инструкции объявления.  
  
 **Идентификатор ошибки:** BC30925  
  
### Исправление ошибки  
  
-   Решите, каким должен быть уровень доступа класса, и удалите все конфликтующие спецификации уровня доступа.  
  
## См. также  
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [Уровни доступа в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)   
 [Оператор Class](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Оператор Structure](/dotnet/visual-basic/language-reference/statements/structure-statement)   
 [НЕ В СБОРКЕ. Классы: схемы объектов](http://msdn.microsoft.com/ru-ru/2c86373d-0333-4616-a7d8-4790c4e89f7b)   
 [Структуры](/dotnet/visual-basic/programming-guide/language-features/data-types/structures)