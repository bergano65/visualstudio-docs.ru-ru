---
title: "&quot;&lt;rsetstmt&gt;&quot; не объявлен | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30821"
  - "vbc30821"
helpviewer_keywords: 
  - "BC30821"
ms.assetid: 7936e3ef-7ac6-4a71-af55-acc2c5cd8754
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;rsetstmt&gt;&quot; не объявлен
"\<rsetstmt\>" не объявлен. Операторы RSet больше не поддерживаются; используйте Microsoft.VisualBasic.RSet.  
  
 Несколько функций, которые были встроенными в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] в предыдущих версиях, были перемещены в пространство имен <xref:Microsoft.VisualBasic?displayProperty=fullName>. Это делает их возможности более доступными для всех языков программирования.  
  
 **Идентификатор ошибки:** BC30821  
  
### Исправление ошибки  
  
-   Используйте функцию `RSet` в пространстве имен `Microsoft.VisualBasic`.  
  
## См. также  
 [НЕ В СБОРКЕ. Функция RSet](http://msdn.microsoft.com/ru-ru/534514e5-dee9-4dfd-993b-da09731eece5)   
 [Programming Element Support Changes Summary](http://msdn.microsoft.com/ru-ru/0483590a-6309-449c-a2fa-effa26a03b95)