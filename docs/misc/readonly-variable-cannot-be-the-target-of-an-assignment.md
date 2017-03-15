---
title: "Переменная ReadOnly не может быть целевым объектом назначения | Microsoft Docs"
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
  - "vbc30064"
  - "bc30064"
helpviewer_keywords: 
  - "BC30064"
ms.assetid: 17e0751d-4c22-40b2-bb07-cb5c845dbc30
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Переменная ReadOnly не может быть целевым объектом назначения
Свойство `ReadOnly` находится в контексте, который назначает ему значение. Во время выполнения значения могут присваиваться только доступным для записи переменным, свойствам и элементам массива.  
  
 **Идентификатор ошибки:** BC30064  
  
### Исправление ошибки  
  
-   Удалите ключевое слово `ReadOnly` из оператора `Dim`, объявляющего переменную, или удалите оператор, который присваивает ей значение.  
  
## См. также  
 [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly)   
 [Оператор Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)