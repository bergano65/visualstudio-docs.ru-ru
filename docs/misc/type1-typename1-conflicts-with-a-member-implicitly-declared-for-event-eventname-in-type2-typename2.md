---
title: "&lt;тип1&gt; &quot;&lt;имя_типа1&gt;&quot; вступает в противоречие с членом, объявленным неявно в &lt;тип1&gt; &quot;&lt;имя_типа2&gt;&quot; для события &quot;&lt;имя_события&gt;&quot; | Microsoft Docs"
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
  - "vbc31061"
  - "bc31061"
helpviewer_keywords: 
  - "BC31061"
ms.assetid: de5b1121-8c8f-4aba-a3e7-1e3e60df0dc5
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;тип1&gt; &quot;&lt;имя_типа1&gt;&quot; вступает в противоречие с членом, объявленным неявно в &lt;тип1&gt; &quot;&lt;имя_типа2&gt;&quot; для события &quot;&lt;имя_события&gt;&quot;
Имя члена типа вступает в противоречие с именем члена, созданного неявно для события. События создают несколько неявных переменных. Например, объявление `Event X` неявно объявляет имена `XEventHandler`, `XEvent`, `add_X` и `remove_X`.  
  
 **Идентификатор ошибки:** BC31061  
  
### Исправление ошибки  
  
-   Переименуйте явно объявленный член, чтобы устранить конфликт имен.  
  
## См. также  
 [NotInBuild. Операторы объявления в Visual Basic](http://msdn.microsoft.com/ru-ru/81f3c398-f45c-4d95-80bf-aa39d1a0fb30)   
 [События](/dotnet/visual-basic/programming-guide/language-features/events/events)