---
title: "Свойство без модификатора ReadOnly или WriteOnly должно предоставлять и процедуру Get, и процедуру Set. | Microsoft Docs"
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
  - "bc30124"
  - "vbc30124"
helpviewer_keywords: 
  - "BC30124"
ms.assetid: b24fc997-9a6b-44d1-b712-dab498a6fc72
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Свойство без модификатора ReadOnly или WriteOnly должно предоставлять и процедуру Get, и процедуру Set.
Если свойство не объявлено как `ReadOnly` или `WriteOnly`, оно должно предоставлять процедуры чтения и записи его значения.  
  
 **Идентификатор ошибки:** BC30124  
  
### Исправление ошибки  
  
1.  Убедитесь, что включили процедуры `Get` и `Set` между операторами `Property` и `End Property`.  
  
2.  Проверьте правильность завершения других процедур в объявлении `Property`.  
  
## См. также  
 [Оператор Property](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Оператор Get](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [Оператор Set](/dotnet/visual-basic/language-reference/statements/set-statement)