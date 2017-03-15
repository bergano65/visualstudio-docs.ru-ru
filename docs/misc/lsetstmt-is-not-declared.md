---
title: "&quot;&lt;lsetstmt&gt;&quot; не объявлен | Microsoft Docs"
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
  - "bc30820"
  - "vbc30820"
helpviewer_keywords: 
  - "BC30820"
ms.assetid: 8666dd52-58ea-4b84-b59a-8ebd8b2cb23b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;lsetstmt&gt;&quot; не объявлен
"\<lsetstmt\>" не объявлен. Операторы LSet больше не поддерживаются; используйте Microsoft.VisualBasic.LSet.  
  
 Несколько функций, которые были встроенными в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] в предыдущих версиях, были перемещены в пространство имен <xref:Microsoft.VisualBasic?displayProperty=fullName>. Это делает их возможности более доступными для всех языков программирования.  
  
 **Идентификатор ошибки:** BC30820  
  
### Исправление ошибки  
  
-   Используйте функцию `LSet` в пространстве имен `Microsoft.VisualBasic`.  
  
## См. также  
 [НЕ В СБОРКЕ. Функция LSet](http://msdn.microsoft.com/ru-ru/591d286c-6b7a-4350-ae74-99fee00fd964)   
 [Programming Element Support Changes Summary](http://msdn.microsoft.com/ru-ru/0483590a-6309-449c-a2fa-effa26a03b95)