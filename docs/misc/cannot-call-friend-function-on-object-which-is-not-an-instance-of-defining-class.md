---
title: "Невозможно вызвать дружественную функцию для объекта, не являющегося экземпляром определяющего класса. | Microsoft Docs"
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
  - "vbrID97"
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Невозможно вызвать дружественную функцию для объекта, не являющегося экземпляром определяющего класса.
Предпринята попытка либо вызова процедуры `Friend` класса, либо получения доступа к дружественному \(`Friend`\) свойству или методу между процессами или между потоками. Процедура `Friend` может вызываться из модуля вне класса, однако она является частью проекта, в котором определен класс.  
  
### Исправление ошибки  
  
-   Убедитесь, что вызов процедуры или доступ к процедуре выполняется из модуля, являющегося частью проекта, в котором определен класс.  
  
## См. также  
 [Friend](/dotnet/visual-basic/language-reference/modifiers/friend)