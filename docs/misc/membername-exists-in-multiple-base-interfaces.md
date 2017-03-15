---
title: "&quot;&lt;имя_пользователя&gt;&quot; присутствует в нескольких базовых интерфейсах | Microsoft Docs"
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
  - "vbc31040"
  - "bc31040"
helpviewer_keywords: 
  - "BC31040"
ms.assetid: c1a80d64-3986-417f-af92-412183e490ad
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;имя_пользователя&gt;&quot; присутствует в нескольких базовых интерфейсах
"\<имя\_пользователя\>" присутствует в нескольких базовых интерфейсах. Используйте имя интерфейса, которое объявляет "\<имя\_пользователя\>" в предложении Implements, а не имя производного интерфейса.  
  
 Этот интерфейс наследует члены с тем же именем из нескольких интерфейсов, что приводит к неоднозначности.  
  
 **Идентификатор ошибки:** BC31040  
  
### Исправление ошибки  
  
-   Используйте в предложениях `Implements` имя заданного интерфейса, а не имя производного интерфейса.  
  
## См. также  
 [Интерфейсы](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)   
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)