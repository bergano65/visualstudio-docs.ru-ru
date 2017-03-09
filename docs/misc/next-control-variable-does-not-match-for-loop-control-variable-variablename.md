---
title: "Управляющая переменная в операторе &quot;Next&quot; не соответствует управляющей переменной цикла &quot;&lt;имя_переменной&gt;&quot; | Microsoft Docs"
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
  - "vbc30070"
  - "bc30070"
helpviewer_keywords: 
  - "BC30070"
ms.assetid: e9e96008-b053-4fa0-8966-decaad99fecd
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Управляющая переменная в операторе &quot;Next&quot; не соответствует управляющей переменной цикла &quot;&lt;имя_переменной&gt;&quot;
Управляющая переменная в операторе `Next` цикла `For...Next` должна соответствовать переменной в операторе `For`.  
  
 **Идентификатор ошибки:** BC30070  
  
### Исправление ошибки  
  
1.  Проверьте правильность написания переменной в операторе `Next` и соответствующем операторе `For`.  
  
2.  Убедитесь в том, что ни одна из частей внешнего цикла не была случайно удалена.  
  
3.  Если этот цикл является частью набора вложенных циклов, убедитесь, что каждый цикл завершен правильно.  
  
## См. также  
 [Оператор For...Next](/dotnet/visual-basic/language-reference/statements/for-next-statement)