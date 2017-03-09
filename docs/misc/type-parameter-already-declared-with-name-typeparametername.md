---
title: "Параметр типа уже объявлен с именем &quot;&lt;имя_параметра_типа&gt;&quot; | Microsoft Docs"
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
  - "vbc32049"
  - "bc32049"
helpviewer_keywords: 
  - "BC32049"
ms.assetid: d7affad0-0c3d-4fce-a1c2-a17f65514471
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Параметр типа уже объявлен с именем &quot;&lt;имя_параметра_типа&gt;&quot;
Параметр универсального типа объявлен с таким же именем, что и у другого параметра того же универсального типа.  
  
 В списке параметров универсального типа каждый параметр должен иметь имя, не совпадающее ни с одним из следующих имен:  
  
-   с именем каждого из других параметров типов в том же списке параметров типов;  
  
-   с именем параметра из списка параметров типов любого имеющегося универсального типа;  
  
-   с именем самого универсального типа.  
  
 **Идентификатор ошибки:** BC32049  
  
### Исправление ошибки  
  
-   Переименуйте параметр типа, чтобы он отличался от всех имен, указанных на этой странице справки.  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Список типов](/dotnet/visual-basic/language-reference/statements/type-list)