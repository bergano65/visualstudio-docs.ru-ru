---
title: "Тип в модуле не может объявляться как &quot;&lt;спецификатор&gt;&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30735"
  - "bc30735"
helpviewer_keywords: 
  - "BC30735"
ms.assetid: df94d581-7f5b-4d42-ae2b-1ef912f133cc
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Тип в модуле не может объявляться как &quot;&lt;спецификатор&gt;&quot;
Внутри модуля объявлен тип с недопустимыми модификаторами.  
  
 **Идентификатор ошибки:** BC30735  
  
### Исправление ошибки  
  
-   Не используйте модификаторы `Protected` и `Protected Friend` для типов, объявленных внутри модуля.  
  
## См. также  
 [Оператор Module](/dotnet/visual-basic/language-reference/statements/module-statement)   
 [Оператор Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)