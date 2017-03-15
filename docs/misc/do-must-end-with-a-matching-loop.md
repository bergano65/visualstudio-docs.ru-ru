---
title: "Блок Do должен заканчиваться соответствующим оператором Loop | Microsoft Docs"
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
  - "vbc30083"
  - "bc30083"
helpviewer_keywords: 
  - "BC30083"
ms.assetid: b157b9e3-57fa-4324-a13d-b37bcf0861e6
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Блок Do должен заканчиваться соответствующим оператором Loop
Оператор `Do` не имеет соответствующего оператора `Loop`. Оператор `Loop` должен использоваться для завершения цикла `Do`.  
  
 **Идентификатор ошибки:** BC30083  
  
### Исправление ошибки  
  
-   Если этот цикл `Do` является частью набора вложенных циклов, убедитесь, что каждый цикл завершен правильно.  
  
-   Добавьте оператор `Loop` в конец цикла `Do`.  
  
## См. также  
 [Оператор Do...Loop](/dotnet/visual-basic/language-reference/statements/do-loop-statement)