---
title: "&quot;&lt;имя_переменной&gt;&quot; не является локальной переменной или параметром, поэтому не может использоваться как переменная оператора &quot;Catch&quot; | Microsoft Docs"
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
  - "bc31082"
  - "vbc31082"
helpviewer_keywords: 
  - "BC31082"
ms.assetid: de197563-5848-4c1a-a519-cc4b5ea9a4c9
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;имя_переменной&gt;&quot; не является локальной переменной или параметром, поэтому не может использоваться как переменная оператора &quot;Catch&quot;
Переменные в операторах `Try...Catch...Finally` должны быть объявлены локально или представлять собой параметры текущей процедуры.  
  
 **Идентификатор ошибки:** BC31082  
  
### Исправление ошибки  
  
1.  Объявите локальные переменные или параметры для операторов `Try...Catch...Finally`.  
  
## См. также  
 [Оператор Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)