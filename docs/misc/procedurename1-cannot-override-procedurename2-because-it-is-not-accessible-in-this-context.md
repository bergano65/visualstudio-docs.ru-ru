---
title: "Процедура &quot;&lt;имя_процедуры1&gt;&quot; не может переопределить процедуру &quot;&lt;имя_процедуры2&gt;&quot;, поскольку она недоступна в данном контексте. | Microsoft Docs"
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
  - "bc31417"
  - "vbc31417"
helpviewer_keywords: 
  - "BC31417"
ms.assetid: 1a36acbf-cead-43a0-b12f-f52f94d09124
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Процедура &quot;&lt;имя_процедуры1&gt;&quot; не может переопределить процедуру &quot;&lt;имя_процедуры2&gt;&quot;, поскольку она недоступна в данном контексте.
Процедура или свойство переопределяет процедуру или свойство с уровнем доступа, который запрещает доступ для переопределения процедуры или свойства.  
  
 Например, если процедура объявлена как `Friend` в одной сборке, она не может быть доступна вне этой сборки. Если процедура в другой сборке в том же проекте попытается переопределить процедуру `Friend`, она не сможет получить к ней доступ для ее переопределения.  
  
 **Идентификатор ошибки:** BC31417  
  
### Исправление ошибки  
  
-   Переместите переопределяющую процедуру или свойство в ту же сборку, где находится переопределяемая процедура или свойство.  
  
     \-или\-  
  
-   Удалите ключевое слово `Overrides`.  
  
## См. также  
 [Уровни доступа в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)   
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)   
 [НЕ В СБОРКЕ. Переопределение свойств и методов](http://msdn.microsoft.com/ru-ru/2167e8f5-1225-4b13-9ebd-02591ba90213)