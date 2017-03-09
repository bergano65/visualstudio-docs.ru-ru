---
title: "Использование атрибута невозможно, так как для него отсутствует конструктор Public. | Microsoft Docs"
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
  - "vbc30758"
  - "bc30758"
helpviewer_keywords: 
  - "BC30758"
ms.assetid: b72d1ff2-f6b2-4a89-9ac2-8765f77bcc97
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Использование атрибута невозможно, так как для него отсутствует конструктор Public.
Конструктор используемого атрибута задан как `Private` и не может использоваться.  
  
 **Идентификатор ошибки:** BC30758  
  
### Исправление ошибки  
  
1.  При появлении этой ошибки с пользовательским атрибутом, который вы разработали, измените модификатор доступа его конструктора `Sub``New` на `Public`.  
  
## См. также  
 [НЕ В СБОРКЕ. Атрибуты в Visual Basic](http://msdn.microsoft.com/ru-ru/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [Время существования: создание и уничтожение объектов](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)