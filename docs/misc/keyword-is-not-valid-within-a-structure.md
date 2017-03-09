---
title: "Ключевое слово &quot;&lt;ключевое_слово&gt;&quot; недопустимо в структуре | Microsoft Docs"
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
  - "bc30044"
  - "vbc30044"
helpviewer_keywords: 
  - "BC30044"
ms.assetid: 252510cf-e084-47e4-9592-4aa8f94fabe4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ключевое слово &quot;&lt;ключевое_слово&gt;&quot; недопустимо в структуре
Структуры являются типами значений, а не ссылочными типами. Структура не является экземпляром, созданным из класса, поэтому ключевые слова `Me`, `MyClass` и `MyBase` не имеют смысла в структуре.  
  
 **Идентификатор ошибки:** BC30044  
  
### Исправление ошибки  
  
-   Измените структуру на класс или удалите ключевое слово из процедуры.  
  
## См. также  
 [Me](http://msdn.microsoft.com/ru-ru/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [MyClass — удалить](http://msdn.microsoft.com/ru-ru/5db36f9b-f796-4b6a-ba34-cac1fde6eb62)   
 [MyBase — удалить](http://msdn.microsoft.com/ru-ru/52491d06-6451-4f6f-9aa6-8fab59bbc2b9)   
 [Основы наследования](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)