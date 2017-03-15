---
title: "Ограничение типа не может быть &quot;NotInheritable&quot;. | Microsoft Docs"
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
  - "vbc32060"
  - "bc32060"
helpviewer_keywords: 
  - "BC32060"
ms.assetid: f45cc0b6-7df1-462a-b3df-c526c143e16a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ограничение типа не может быть &quot;NotInheritable&quot;.
Список ограничений включает класс, помеченный как [NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable).  
  
 Список ограничений для параметра типа может принимать не более одного класса. Аргумент типа, предоставленный для этого параметра типа, должен наследовать от этого класса. Таким образом, параметр типа не может принимать в качестве ограничения *запечатанный*, или `NotInheritable`, класс.  
  
 **Идентификатор ошибки:** BC32060  
  
### Исправление ошибки  
  
-   Если параметр типа должен иметь возможность наследования от класса, и вы можете управлять определением класса, то удалите объявление `NotInheritable` из этого класса.  
  
-   Если класс должен оставаться `NotInheritable`, его нельзя использовать как ограничение. Удалите имя этого класса из списка ограничений.  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)