---
title: "Свойства, объявленные как доступные только для чтения (&quot;ReadOnly&quot;), не могут иметь процедуру &quot;Set&quot; | Microsoft Docs"
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
  - "vbc30022"
  - "bc30022"
helpviewer_keywords: 
  - "BC30022"
ms.assetid: a22eff96-8c18-47c4-9ef0-f98b2ab8a5d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Свойства, объявленные как доступные только для чтения (&quot;ReadOnly&quot;), не могут иметь процедуру &quot;Set&quot;
Процедура `Set` записывает значение свойства. Запись в свойства `ReadOnly` невозможна.  
  
 **Идентификатор ошибки:** BC30022  
  
### Исправление ошибки  
  
-   Удалите ключевое слово `ReadOnly` из оператора `Property` или удалите процедуру `Set` из тела свойства.  
  
## См. также  
 [Оператор Property](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Оператор Set](/dotnet/visual-basic/language-reference/statements/set-statement)   
 [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly)