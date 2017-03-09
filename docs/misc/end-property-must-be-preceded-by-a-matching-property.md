---
title: "Оператору &quot;End Property&quot; должен предшествовать соответствующий оператор &quot;Property&quot;. | Microsoft Docs"
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
  - "vbc30431"
  - "bc30431"
helpviewer_keywords: 
  - "BC30431"
ms.assetid: b1e02d97-b38a-4acf-b351-1726f17a0051
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Оператору &quot;End Property&quot; должен предшествовать соответствующий оператор &quot;Property&quot;.
Оператору `End Property` в коде не предшествует соответствующее объявление `Property`.  
  
 **Идентификатор ошибки:** BC30431  
  
### Исправление ошибки  
  
-   Удалите оператор `End Property`, если он лишний.  
  
-   Добавьте процедуру `Property`, если она отсутствует.  
  
-   Переместите оператор `End Property` в соответствующее место кода.  
  
## См. также  
 [НЕ В СБОРКЕ. Свойства и процедуры свойств](http://msdn.microsoft.com/ru-ru/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [Оператор End \<ключевое\_слово\>](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)