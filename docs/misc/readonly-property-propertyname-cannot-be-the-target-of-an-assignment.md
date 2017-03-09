---
title: "Доступному только для чтения (ReadOnly) свойству &quot;&lt;имя_свойства&gt;&quot; не может присваиваться значение. | Microsoft Docs"
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
  - "bc30098"
  - "vbc30098"
helpviewer_keywords: 
  - "BC30098"
ms.assetid: d0c6cdac-a49d-49d2-ba92-ddf01eed0620
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Доступному только для чтения (ReadOnly) свойству &quot;&lt;имя_свойства&gt;&quot; не может присваиваться значение.
Свойство с атрибутом `ReadOnly` находится в контексте, который присваивает ему значение. Во время выполнения значения могут присваиваться только доступным для записи переменным, свойствам и элементам массива.  
  
 **Идентификатор ошибки:** BC30098  
  
### Исправление ошибки  
  
-   Удалите ключевое слово `ReadOnly` из оператора `Property`, объявляющего переменную, или удалите оператор, который присваивает значение.  
  
## См. также  
 [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly)   
 [Оператор Property](/dotnet/visual-basic/language-reference/statements/property-statement)