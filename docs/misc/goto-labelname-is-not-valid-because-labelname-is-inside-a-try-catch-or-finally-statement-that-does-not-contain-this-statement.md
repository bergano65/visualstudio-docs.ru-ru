---
title: "Оператор &quot;GoTo &lt;имя_метки&gt;&quot; является недопустимым, так как &quot;&lt;имя_метки&gt;&quot; находится в теле оператора &quot;Try&quot;, &quot;Catch&quot; или &quot;Finally&quot;, не содержащего этот оператор | Microsoft Docs"
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
  - "bc30754"
  - "vbc30754"
helpviewer_keywords: 
  - "BC30754"
ms.assetid: 2eefc7fb-fdf0-41e9-bf60-c3bc93580e14
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператор &quot;GoTo &lt;имя_метки&gt;&quot; является недопустимым, так как &quot;&lt;имя_метки&gt;&quot; находится в теле оператора &quot;Try&quot;, &quot;Catch&quot; или &quot;Finally&quot;, не содержащего этот оператор
Нельзя осуществлять ветвление в блок `Try...Catch...Finally`.  
  
 **Идентификатор ошибки:** BC30754  
  
### Исправление ошибки  
  
-   Перестройте ваш код, чтобы метка располагалась перед блоком `Try...Catch...Finally`.  
  
## См. также  
 [Оператор Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)