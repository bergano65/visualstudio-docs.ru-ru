---
title: "Параметр типа &quot;&lt;имя_параметра_типа&gt;&quot; может иметь только одно ограничение, являющееся классом | Microsoft Docs"
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
  - "bc32047"
  - "vbc32047"
helpviewer_keywords: 
  - "BC32047"
ms.assetid: ac7ab76b-5300-4c79-b519-5a1287ed5fa9
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Параметр типа &quot;&lt;имя_параметра_типа&gt;&quot; может иметь только одно ограничение, являющееся классом
Список ограничений содержит несколько классов.  
  
 Список ограничений в параметре типа может принимать любое количество интерфейсов, но не более одного класса. Аргумент типа, предоставленный для этого параметра типа, должен наследовать от этого класса, и [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] не поддерживает множественное наследование.  
  
 **Идентификатор ошибки:** BC32047  
  
### Исправление ошибки  
  
-   Выберите один класс и включите в список ограничений только этот класс.  
  
-   Вы могли бы определить дополнительные параметры типа для размещения класса или классов, которые не удалось включить в данный список ограничений.  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)