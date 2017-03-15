---
title: "Слишком много аргументов типа для метода расширения &quot;&lt;имя_метода&gt;&quot;, определенного в &quot;&lt;имя_типа&gt;&quot;. | Microsoft Docs"
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
  - "bc36591"
  - "vbc36591"
helpviewer_keywords: 
  - "BC36591"
ms.assetid: 504c9b1f-f511-4198-8970-136d1a1bdafe
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Слишком много аргументов типа для метода расширения &quot;&lt;имя_метода&gt;&quot;, определенного в &quot;&lt;имя_типа&gt;&quot;.
Универсальный метод расширения был вызван с большим числом аргументов типа, чем число параметров типа.  
  
 При вызове универсального метода вы должны предоставить по одному аргументу типа для каждого параметра типа, определяемого этим методом.  
  
 **Идентификатор ошибки:** BC36591  
  
### Исправление ошибки  
  
-   Удалите аргументы типа из списка аргументов типа так, чтобы имелось по одному аргументу типа для каждого параметра типа, определенного универсальным методом, который вы вызываете.  
  
## См. также  
 [Методы расширения](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Список типов](/dotnet/visual-basic/language-reference/statements/type-list)