---
title: "Свойство с модификатором &quot;ReadOnly&quot; должно обеспечивать процедуру &quot;Get&quot; | Microsoft Docs"
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
  - "bc30126"
  - "vbc30126"
helpviewer_keywords: 
  - "BC30126"
ms.assetid: a522c39e-1f11-45c8-a00b-3546c842909a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Свойство с модификатором &quot;ReadOnly&quot; должно обеспечивать процедуру &quot;Get&quot;
Если свойство объявлено как `ReadOnly`, то оно должно предоставить процедуру для чтения его значения.  
  
 **Идентификатор ошибки:** BC30126  
  
### Исправление ошибки  
  
1.  Включите процедуру `Get` между операторами `Property` и `End Property`.  
  
2.  Проверьте правильность завершения других процедур в объявлении `Property`.  
  
## См. также  
 [Оператор Property](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Оператор Get](/dotnet/visual-basic/language-reference/statements/get-statement)