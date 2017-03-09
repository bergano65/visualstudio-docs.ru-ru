---
title: "&quot;&lt;ключевое_слово&gt;&quot; является допустимым только в пределах класса | Microsoft Docs"
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
  - "bc32002"
  - "vbc32002"
helpviewer_keywords: 
  - "BC32002"
ms.assetid: 773d8d50-abb8-4257-83a5-6e017c199d82
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;ключевое_слово&gt;&quot; является допустимым только в пределах класса
Вне определения класса используется ключевое слово, относящееся к классам, например `Me` или `MyClass`.  
  
 **Идентификатор ошибки:** BC32002  
  
### Исправление ошибки  
  
-   Если код, в котором используется ключевое слово, содержит экземпляры класса, переместите его в реализацию класса.  
  
-   Если код, в котором используется ключевое слово, не относится к классам, удалите недопустимое ключевое слово.  
  
## См. также  
 [Me](http://msdn.microsoft.com/ru-ru/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [MyClass — удалено](http://msdn.microsoft.com/ru-ru/5db36f9b-f796-4b6a-ba34-cac1fde6eb62)   
 [Оператор Class](/dotnet/visual-basic/language-reference/statements/class-statement)