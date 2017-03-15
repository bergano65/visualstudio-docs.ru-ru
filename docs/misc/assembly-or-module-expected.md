---
title: "Требуется Assembly или Module | Microsoft Docs"
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
  - "vbc32015"
  - "bc32015"
helpviewer_keywords: 
  - "BC32015"
ms.assetid: 6e62fe8d-a875-4995-b6b2-443e75c65e85
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Требуется Assembly или Module
Глобальный атрибут задан без указания того, применяется ли он для всей сборки или только для текущего модуля. Для глобальных атрибутов необходимо указать `Assembly` или `Module`.  
  
 Глобальным атрибутом является тот, который присутствует в строке исходного кода сам по себе, а не применяется к объявлению конкретного программного элемента.  
  
 **Идентификатор ошибки:** BC32015  
  
### Исправление ошибки  
  
1.  Если необходимо сделать атрибут глобальным, добавьте в начало блока атрибута ключевое слово `Assembly` или `Module`, за которым следует двоеточие \(:\).  
  
2.  Если не требуется делать атрибут глобальным, удалите блок атрибута или перенесите его в объявление программного элемента.  
  
## См. также  
 [Assembly](/dotnet/visual-basic/language-reference/modifiers/assembly)   
 [Module \<ключевое\_слово\>](../Topic/Module%20%3Ckeyword%3E%20\(Visual%20Basic\).md)   
 [НЕ В СБОРКЕ. Применение атрибутов](http://msdn.microsoft.com/ru-ru/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [НЕ В СБОРКЕ. Глобальные атрибуты в Visual Basic](http://msdn.microsoft.com/ru-ru/253a32d8-1531-4504-b687-088554ab71d2)